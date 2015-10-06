# stream_command

This is my attempt to figure out a good pattern for streaming the results of a Command. For my specific use case what I really want a mixed stream of `stderr` and `stdout`. This is so I can get a live stream of exactly what a terminal would see when I'm executing a long running process such as an `ansible-playbook` run.

The dumbest way I can do this is to open a temporary file, point stdout and stderr at that file descriptor and read from that file as it gets written to. This ensures that the stream will be ordered properly but it does involve creating a temporary file which seems silly.

What would be great is if I can figure out a way to use `Command::spawn` and read from the resulting `ChildStdout` and `ChildStderr` without having to fuck around with temp files. I'm gonna experiment with different setups for `Command#stderr` and `Command#stdout`.

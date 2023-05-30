# Audit trail tools

## Task management

[Taskwarrior](http://taskwarrior.org/) is a popular task manager with many features for managing large task lists in a quick and efficient manner.

Taskwarrior is useful for managing large numbers of tasks. It provides reports, searching, sorting, and various levels of customizable detail. It maintains timestamps and unique identifiers (UUID) for each task, manages prioritisation of pending tasks, and keeps a history of completed tasks. The ability to create user-defined attributes makes it customisable for specific settings, such as a forensics lab or examination process.

You can also maintain a list of completed tasks and pending work by editing a simple text file. An example is the [todo.txt file format](http://todotxt.com/) by Gina Trapani.

You can also maintain an examiner activity log of completed tasks without the use of task management software. For example, here is a simple shell alias that redirects a short description into a file with a timestamp:

```shell
alias log="echo $2 \`date +%FT%R\` >> ~/examiner.log"
```

Then use it with, for example:

```shell
log started forensic acquisition of the disks
```
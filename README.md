# Exercise description

The goal of the exercise is to show ones ability to profile a simple executable using the CPU Profiler in [Google Performance Tools](https://gperftools.github.io/gperftools/cpuprofile.html), produce a callgrind output file with the format described at <http://valgrind.org/docs/manual/cl-format.html>, and convert it in a SQLITE database with [the schema already used by igprof-navigator](https://github.com/igprof/igprof/blob/master/src/igpython-analyse#L9) web frontend. 

# Prerequisites

* You must be able to install SQLite / Google Performance Tools (GPT) on your Linux / BSD / Mac distribution of choice.
* You must write / use a small C / C++ program which is complex enough to provide a dozen of entries in a profile report.
* You must run your program and be able to profile it with GPT, producing a callgrind output as documented.

# Actual coding task

Once you have a callgrind output, you need to write a program in either C++, Python, or Javascript (NodeJS) to process such an an output and create an Sqlite database with the schema mentioned in the "Exercise description" above.

# Suggestions

* Keep the test program simple and do not spend much time on it. You only need to have a few nested calls invoking some mathematical function (e.g. exp(1)) in a loop to simulate a performance payload. 
* sqlite can read commands from `stdin`. Rather than using an API, simply printout the SQL statements on stdout and pipe them to sqlite. E.g.:

```bash
your-conversion-script -i <your-input-callgrind-file> | sqlite3 yoursqlitedb.db
```

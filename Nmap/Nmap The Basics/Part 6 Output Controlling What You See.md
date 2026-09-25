
### Verbosity and Debugging
`nmap <ip> -v` ---> show more output while scanning in real time, meaning without the output will be nothing when scanning
Most likely, the `-v` option is more than enough for verbose output; however, if you are still unsatisfied, you can increase the verbosity level by adding another “v” such as `-vv` or even `-vvvv`. You can also specify the verbosity level directly, for example, `-v2` and `-v4`. You can even increase the verbosity level by pressing “v” after the scan already started.
#### Debugging
If all this verbosity does not satisfy your needs, you must consider the `-d` for debugging-level output. Similarly, you can increase the debugging level by adding one or more “d” or by specifying the debugging level directly. The maximum level is `-d9`; before choosing that, make sure you are ready for thousands of information and debugging lines.

### Saving Scan Report
- `nmap <ip> -oN <filename>` - Normal output
- `nmap <ip> -oX <filename>` - XML output
- `nmap <ip> -oG <filename>` - `grep`-able output (useful for `grep` and `awk`)
- `nmap <ip> -oA <basename>` - Output in all major formats
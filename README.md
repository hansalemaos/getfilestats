# Retrieves statistics from files (os.stat) e returns a pandas DataFrame 

## pip install getfilestats

### Tested against Windows 10 / Python 3.10 / Anaconda

The module utilizes various methods from the pandas library and the os.stat function from the os module to gather information about each file's attributes, including attributes such as file size, timestamps, permissions, and more.

This code can be useful for individuals who need to analyze and gather information about multiple files simultaneously. For example, it can be used by data scientists to collect metadata about a large number of files in a directory for further analysis. It can also be utilized by system administrators or file management tools to retrieve and organize file statistics for monitoring, auditing, or reporting purposes.

### How to use it:


```python
    Retrieve statistics from all files in the specified folders.

    Args:
    - folders: The folder path(s) to search for files. Can be a single string or a list/tuple of strings.
    - allowed_extensions: Optional. A string or a list/tuple of allowed file extensions. Default is an empty tuple (all extensions are allowed).
    - maxsubfolders: Optional. The maximum number of subfolders to search within each folder. Default is -1 (unlimited).

    Returns:
    A pandas DataFrame containing the statistics for each file found.

    Example:

import pandas as pd
from getfilestats import get_stats_from_all_files_in_folders
df = get_stats_from_all_files_in_folders(
	folders=r"C:\cygwinxx",
	allowed_extensions=(".exe", ".bat"),
	maxsubfolders=-1
)
print(df1[:5].to_string())


#                         filepath           st_atime          st_atime_ns           st_ctime          st_ctime_ns      st_dev  st_file_attributes  st_gid           st_ino  st_mode           st_mtime          st_mtime_ns  st_nlink  st_reparse_tag  st_size  st_uid
# 0         C:\cygwinxx\Cygwin.bat  1680571708.307696  1680571708307696300  1680571708.306699  1680571708306699200  3067733448                  32       0  281474978447139    33279  1680571708.307696  1680571708307696300         1               0       88       0
# 1  C:\cygwinxx\bin\addftinfo.exe  1680571700.969256  1680571700969256300  1680571700.968287  1680571700968286400  3067733448                  32       0  281474978444793    33279       1554031577.0  1554031577000000000         1               0    51219       0
# 2  C:\cygwinxx\bin\addr2line.exe    1680571785.0613  1680571785061300100  1680571785.059305  1680571785059304700  3067733448                  32       0  281474978447991    33279       1676205497.0  1676205497000000000         1               0  1108499       0
# 3    C:\cygwinxx\bin\apngasm.exe  1680573545.995065  1680573545995064900  1680573545.989051  1680573545989051100  3067733448                  32       0  562949955151788    33279       1423742864.0  1423742864000000000         1               0    97076       0
# 4         C:\cygwinxx\bin\ar.exe  1680571785.064319  1680571785064319100  1680571785.062297  1680571785062296800  3067733448                  32       0  281474978447992    33279       1676205500.0  1676205500000000000         2               0  1136147       0



import pandas as pd
from getfilestats import get_stats_from_files
df = get_stats_from_files([
	r"C:\cygwinxx\bin\sphinx-autogen",
	r"C:\cygwinxx\bin\apt.sh",
	r"C:\cygwinxx\bin\pip3",
	r"C:\cygwinxx\bin\pydoc3",
	r"C:\cygwinxx\bin\python",
	r"C:\cygwinxx\bin\python3",
	r"C:\cygwinxx\bin\sphinx-apidoc",
])

print(df2[:5].to_string())

#                          filepath           st_atime          st_atime_ns           st_ctime          st_ctime_ns      st_dev  st_file_attributes  st_gid            st_ino  st_mode           st_mtime          st_mtime_ns  st_nlink  st_reparse_tag  st_size  st_uid
# 0  C:\cygwinxx\bin\sphinx-autogen  1680571840.266463  1680571840266462600  1680571840.266463  1680571840266462600  3067733448                   4       0  3659174697372682    33206  1680571840.266463  1680571840266462600         1               0       78       0
# 1          C:\cygwinxx\bin\apt.sh  1680571842.981623  1680571842981622600  1680571842.981623  1680571842981622600  3067733448                  32       0  1970324838741762    33206  1680571842.981623  1680571842981622600         1               0    18531       0
# 2            C:\cygwinxx\bin\pip3  1680571840.387299  1680571840387298800  1680571840.387299  1680571840387298800  3067733448                   4       0  3659174697374415    33206  1680571840.387299  1680571840387298800         1               0       58       0
# 3          C:\cygwinxx\bin\pydoc3  1680571840.506555  1680571840506555000  1680571840.506555  1680571840506555000  3067733448                   4       0  3940649674085961    33206  1680571840.506555  1680571840506555000         1               0       62       0
# 4          C:\cygwinxx\bin\python  1680571840.458692  1680571840458691500  1680571840.458692  1680571840458691500  3067733448                   4       0  3377699720663980    33206  1680571840.458692  1680571840458691500         1               0       62       0


```

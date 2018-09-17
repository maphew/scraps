# Distribution Not Found Error

Why does this simple program result in a `pkg_resources.DistributionNotFound` error and how do we fix it?

# Build

    pushd D:\code-maphew\scraps\bug-dist-not-found
    python setup.py install --root=target --prefix=usr

```python
running install
running build
running build_py
package init file 'my_project\__init__.py' not found (or not a regular file)
creating build
creating build\lib
creating build\lib\my_project
copying my_project\__main__.py -> build\lib\my_project
running install_lib
creating target
creating target\usr
creating target\usr\Lib
creating target\usr\Lib\site-packages
creating target\usr\Lib\site-packages\my_project
copying build\lib\my_project\__main__.py -> target\usr\Lib\site-packages\my_project
byte-compiling target\usr\Lib\site-packages\my_project\__main__.py to __main__.cpython-36.pyc
running install_egg_info
running egg_info
creating my_project.egg-info
writing my_project.egg-info\PKG-INFO
writing dependency_links to my_project.egg-info\dependency_links.txt
writing entry points to my_project.egg-info\entry_points.txt
writing top-level names to my_project.egg-info\top_level.txt
writing manifest file 'my_project.egg-info\SOURCES.txt'
reading manifest file 'my_project.egg-info\SOURCES.txt'
writing manifest file 'my_project.egg-info\SOURCES.txt'
Copying my_project.egg-info to target\usr\Lib\site-packages\my_project-0.1.0-py3.6.egg-info
running install_scripts
Installing my_project-script.py script to target\usr\Scripts
Installing my_project.exe script to target\usr\Scripts
```

# Run

    pushd D:\code-maphew\scraps\bug-dist-not-found
    .\target\usr\Scripts\my_project.exe

```python
Traceback (most recent call last):
  File "D:\code-maphew\scraps\bug-dist-not-found\target\usr\Scripts\my_project-script.py", line 6, in <module>
    from pkg_resources import load_entry_point
  File "C:\ArcGIS\Pro\bin\Python\envs\arcgispro-py3\lib\site-packages\pkg_resources\__init__.py", line 3105, in <module>
    @_call_aside
  File "C:\ArcGIS\Pro\bin\Python\envs\arcgispro-py3\lib\site-packages\pkg_resources\__init__.py", line 3089, in _call_aside
    f(*args, **kwargs)
  File "C:\ArcGIS\Pro\bin\Python\envs\arcgispro-py3\lib\site-packages\pkg_resources\__init__.py", line 3118, in _initialize_master_working_set
    working_set = WorkingSet._build_master()
  File "C:\ArcGIS\Pro\bin\Python\envs\arcgispro-py3\lib\site-packages\pkg_resources\__init__.py", line 578, in _build_master
    ws.require(__requires__)
  File "C:\ArcGIS\Pro\bin\Python\envs\arcgispro-py3\lib\site-packages\pkg_resources\__init__.py", line 895, in require
    needed = self.resolve(parse_requirements(requirements))
  File "C:\ArcGIS\Pro\bin\Python\envs\arcgispro-py3\lib\site-packages\pkg_resources\__init__.py", line 781, in resolve
    raise DistributionNotFound(req, requirers)
pkg_resources.DistributionNotFound: The 'my-project==0.1.0' distribution was not found and is required by the application
```



### References

* https://github.com/leo-editor/leo-editor/issues/968
* https://stackoverflow.com/questions/35457144/pkg-resources-distributionnotfound-when-using-a-module-installed-from-a-bdist-rp
* https://stackoverflow.com/questions/52375693/troubleshooting-pkg-resources-distributionnotfound-error





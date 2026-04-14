## VCSTool
vcs import is a command in VCSTool, a version control system tool used in ROS 2 to manage multiple repositories. It allows you to clone or update multiple repositories based on a .repos file, which specifies repository URLs, branches, and commit hashes.
How vcs import Works

- It reads a .repos file that contains information about repositories.
- It clones or checks out the specified repositories into the target directory.

Typical Use Case

You often use vcs import to set up a workspace in ROS 2, ensuring that all necessary repositories are pulled with the correct versions.

Example
```sh
vcs import src < ros2.repos
```

Example .repos File format (yaml)
```yaml
repositories:
  realsense2_camera:
    type: git
    url: https://github.com/IntelRealSense/realsense-ros.git
    version: humble
  some_other_package:
    type: git
    url: https://github.com/example/some_package.git
    version: main
```

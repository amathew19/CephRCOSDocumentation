# IBM Ceph RCOS Documentation - Fall 2024

## Hurdles that you've run into
### Development Environment Setup
- Encountered issues setting up the environment on a VirtualBox VM without a VPN, which led to crashes and performance problems.
- Had to troubleshoot and reinstall configurations multiple times to stabilize the setup.

### Navigating a Large Codebase
- Had challenges starting with a large codebase, especially since it was my first experience on such a scale
- Was concerned about unintentionally breaking existing code.
- Spent extra time understanding the code structure and dependencies before making changes.

### VPN Configuration
- Faced difficulties connecting to a remote machine using OpenVPN for secure access.
- Required assistance to properly configure the VPN and resolve connection issues.

### Working with Ninja Build System
- Needed to create build files with Ninja, a CMake wrapper, which required learning new workflows.
- Had to consult documentation and examples to understand the specifics of Ninja’s syntax and usage.

### Git Workflow Proficiency
- Limited experience with certain Git commands, specifically around using fork, rebase, and merge.
- Practiced these commands on smaller test branches to gain confidence before applying them on the main codebase.
- Understanding of CI/CD pipelines


## Hurdles that you've ultimately overcome
Setting my development environment
Setting up a VPN
Have a working knowledge of Git methods like fork, branch, checkout, etc. 


## Project brainstorming ideas
### Project 3 - Exten mgr CLI command output for disabled modules (Team)
- Hashmap to efficiently track and store pointers to module states and their dependencies
- Extensive command testing to identify and understand exactly why enabled modules weren't showing up
- Memoization to cache results, making it way faster by avoiding repeat calculations

### Feature #22442 - ceph daemon mon.id mon_status -> ceph daemon mon.id status (Self)
 - 


## How you set up your development environment
 - Downloaded VirtualBox from https://www.virtualbox.org/ and install
 - Download a Ubuntu image (.iso) file from https://ubuntu.com/download/desktop 
 - Created a virtual machine by following these steps from https://ubuntu.com/tutorials/how-to-run-ubuntu-desktop-on-a-virtual-machine-using-virtualbox#2-create-a-new-virtual-machine (Note: Make sure you uncheck the “Skip Unattended Installation” option (bug – more details below))
 - Clone the Ceph repo
 - Ran this command: `./install-deps.sh` (installs all the dependencies)
 - Next, ran this command: `./do_cmake.sh -DCMAKE_BUILD_TYPE=RelWithDebInfo` (creates a build directory)
 - Then, `cd build` (changing to the build directory)
 - Next, `ninja vstart-base cephfs cython_cephfs cython_rbd` 


## Things you've learned about Ceph so far
- Ceph is a powerful distributed storage solution for effeicent data storage and retrieval

## Things you've learned about git
Forking a repository
Creating a branch


## Things you've learned about committing to open source projects
- Pair Programming
- The importance of creating a fork of the main repository


## Ubuntu Unattended Installation Bug
Stumbled on a bug where I found unattended installation does not add the user to the list of sudo/root users. 

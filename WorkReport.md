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

### Terminal-based IDEs (vim and nano)
- Limited experience working with vim and nano


## Hurdles That I've Ultimately Overcome  
 ### Setting up my development environment:  
   - Resolved version compatibility issues with essential tools and libraries.  
   - Configured my IDE and build system for efficient workflow.  
   - Tested the setup to ensure smooth integration with project repositories.  

 ### Setting up a VPN:  
   - Addressed frequent disconnection and authentication errors.  
   - Configured VPN settings to meet specific project requirements.  
   - Verified secure access to restricted resources without compromising performance.  

 ### Learning how to utilize forks to develop features:  
   - Understood the concept of isolating changes in personal forks for independent development.  
   - Practiced managing feature branches for better version control.  
   - Learned how to submit polished pull requests for team review.  


## Project brainstorming ideas
### Project 3 - Exten mgr CLI command output for disabled modules (Team)
- Hashmap to efficiently track and store pointers to module states and their dependencies
- Extensive command testing to identify and understand exactly why enabled modules weren't showing up
- Memoization to cache results, making it way faster by avoiding repeat calculations

### Feature #22442 - ceph daemon mon.id mon_status -> ceph daemon mon.id status (Self)
 - Working on standardizing the command structure across the Ceph monitoring system
 - Understand how the ceph handles daemon commands and processes
 - Support for detailed status output based on specific monitor ID references


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
- Ceph organizes data into clusters, which are grouped into logical pools for efficient data management and access
- Each pool can be configured with different replication policies and performance characteristics to meet specific storage needs

## Things I've Learned About Git  
 ### Forking a repository:  
   - Learned how to create a personal copy of a repository to work on features independently.  
   - Understood how forks allow for safe experimentation without affecting the original project.  

 ### Creating a branch:  
   - Gained insight into isolating changes by creating branches for specific tasks or features.  
   - Learned how to switch between branches and merge them into the main repository efficiently.
         
 ### Git Commands:  
   - 
     
## Things you've learned about committing to open source projects
- Pair Programming
- The importance of creating a fork of the main repository


## Ubuntu Unattended Installation Bug
Stumbled on a bug where I found unattended installation does not add the user to the list of sudo/root users. 

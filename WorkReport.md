# IBM Ceph RCOS Documentation - Fall 2024

## Hurdles that you've run into
### Development Environment Setup
- Encountered issues setting up the environment on a VirtualBox VM without a VPN, which led to crashes and performance problems.
- Had to troubleshoot and reinstall configurations multiple times to stabilize the setup.
- Spent time fine-tuning VM resource allocation with the right balance of memory, CPU cores.

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
- Limited experience working with vim and nano, requiring significant time investment to learn the basics!
- Steep learning curve adapting to vim's modal editing system
- Difficulty remembering common keyboard shortcuts and commands for text manipulation


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

 ### Learning Git and working with Terminal-based IDE's:  
   - Figured out how to handle file editing and navigation in the terminal
   - Got better at Git commands, especially with branching and fixing merge issues
   - Got comfortable with basic vim and nano commands needed for daily coding tasks


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
 - Next, `ninja vstart-base cephfs cython_cephfs cython_rbd`, which compiles and links using the ninja compiler, a CMake wrapper
 - Then, you run the start script to create a cluster, `RGW=0 MDS=0 ../src/start.sh --debug --new -x --localhost --bluestore --without-dashboard`
 - Then you can run the `./bin/ceph -s` OR `ceph -s` command to check your cluster's health.
 - Finally, you can run `../src/stop.sh` to shut down your cluster.


## Things you've learned about Ceph so far
- Ceph is a powerful distributed storage solution for effeicent data storage and retrieval
- Ceph organizes data into clusters, which are grouped into logical pools for efficient data management and access
- Each pool can be configured with different replication policies and performance characteristics to meet specific storage needs
- Ceph has a set of core daemons (like monitors, OSDs, and managers) which are configured for various functionalities such as monitoring, logging, and managing the clusters
- Ceph supports multiple storage interfaces including object storage, block storage, and file storage

## Things I've Learned About Git  
 ### Forking a repository:  
   - Learned how to create a personal copy of a repository to work on features independently, enabling collaboration without direct access to the original project
   - Understood how forks allow for safe experimentation without affecting the original project
   - Mastered the setup of public/private SSH keys for secure authentication when pushing and pulling code from GitHub repositories

 ### Creating a branch:  
   - Gained insight into isolating changes by creating branches for specific tasks or features, keeping the main codebase stable  
   - Learned how to switch between branches and merge them into the main repository efficiently, maintaining a clean project history
         
 ### Git Commands:  
   - `git log`: lists the commit history, showing author, date, and commit messages for tracking project evolution
   - `git reset --hard`: resets the head of the branch to the previous commit, discarding all uncommitted changes
   - `git checkout <branch_name>`:  switches to another branch, allowing you to work on different features in isolation
     
## Things you've learned about committing to open source projects
- Effective Pair Programming: Pair programming sessions created invaluable opportunities for real-time code review and knowledge sharing. These collaborative sessions helped me catch potential issues early.
- Coding Standards: Maintaining consistent code standards which was crucial for project longevity and efficient collaboration. It included writing descriptive commit messages that explain both what changed and why, while following established style guides.
- Iterative Improvement: Starting with smaller, focused pull requests to build trust with maintainers and make the review process more manageable proved to be a smart move.

## Ubuntu Unattended Installation Bug
While setting up a new Ubuntu VM, I encountered a frustrating issue with the unattended installation process. After two reinstalls, I discovered that the automated installer wasn't adding the created user to the sudoers list, effectively blocking them from performing any root-level operations. This quirk in the unattended installation meant my user couldn't execute basic admin tasks without manually modifying the sudoers configuration. I've documented this issue since it seems like a common pitfall that could save others from spending hours troubleshooting like I did.

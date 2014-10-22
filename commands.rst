Commands
========

loop examples
-------------

::

  #copy files from fiven list (list in file) to some location
  for file in `cat my_bad.txt`; do cp tests/$file tests/; done;   
  
  #compile all files
  for file in * ; do gcc -c $file; done;

  #run some command 1000 times
  for i in {1..1000} ;  do  echo *******$i; ./Tester -t Nested && echo ********** ;  done 


find examples
-------------

::

  #find and delete all sym links
  find -type l -exec rm -rf {} + 


  #get symbolic links and store result in file in special format
  find . -type l -exec ls -log --time-style=+ {} + | awk '{print $4" "$5" "$6}' > ~/system_links.txt

  #find executable files
  find . -executable -type f

  #get nr of files in directory
  find llvm/ -type f | wc -l

grep examples
-------------

::

  #grep only given files
  grep -rn "m_AllExprs" . --include=*.cpp 

  #get running time from bootchart log
  grep -ri '<!-- mount' bootchart-20000101-1111.8.svg | tr ' |=' '\|' | cut -d '|' -f 7 

  #sort by run time entries from bootchart log
  grep -ri 'runtime' bootchart-20000101-1111.8.svg | tr ' |=' '\|' | sort -k7n,8 -t '|'

sed examples
------------

::

  sed 's/\[/\n\[/g' systemdanal.dat > new.dat
  version=$($CPPCHECK --version | sed 's/[[:alpha:]| ]*//')

  sed -i 's/rect.blocked  { fill:rgb(255,  0,  0)/rect.blocked  { fill:rgb(0,  255,  0)/g' *.svg

rpm related examples
--------------------

::

  rpm -q --scripts httpd #see preinstall scripts

  rpm -qp --scripts foo.rpm #see postinstall scripts

  rpm2cpio myrpmfile.rpm | cpio -idmv

  rpm -qa | grep -i webmin #look for the full name of rpm pack
  rpm -e --nodeps httpd #uninstall without checking dependenc
  rpm -qf /usr/lib/systemd/system/udev-trigger.service # to which package given file belongs

git examples
------------

::

  git submodule init
  git submodule update


  git branch -m old_branch new_branch #renam branch

  git branch -D bugfix                #delete branch

  git checkout -b test origin/test    # create local branch from remote

  git diff --name-only SHA1 SHA2      #get file names

  //unstage a deleted file in git
  # this restores the file status in the index
  git reset -- <file>
  # then check out a copy from the index
  git checkout -- <file>

  git remote set-url --push origin git@github.com:leo/repox.git #set push address
  git remote set-url --push origin user@server:gitrepo
  CURRENT_BRANCH_NAME=`git rev-parse --abbrev-ref HEAD`
  git log --pretty=%s rev1 rev2 #get commit msgs

  git remote add release /home/gitrepo/repo.git

  git reset --hard HEAD~1

  git rev-parse --symbolic --abbrev-ref $1  #branch name in update hook

  git log master -1 --pretty=format:%H #current hash

  git commit --amend -m "New commit message"

  git rev-list --max-parents=0 HEAD #first init commit id sha (since 1.7.4.2)

  git log cab313ef171e078be808871b6d328b00a0f34e27..HEAD --pretty=format: --name-only --diff-filter=A | sort | uniq #all added files since given rev

  git push -u ../../stage.git master

  git log --author="author" --name-only --pretty=format: | sort | uniq  |  grep -v '^$' # list all files modified by samsung
  cp --parents `git log --author="author" --name-only --pretty=format: | sort | uniq  |  grep -v '^$'` ~/dest/

  #Tagging
  git tag tagname
  git push origin tagname

gcc/g++
-------

::

  ./configure --build=arm-v7a15v3r1-linux-gnueabi #crosscomp

  cd ${build_directory}
  rm -rf *
  cmake -DCMAKE_TOOLCHAIN_FILE=/opt/android-toolchain/android-14.cmake ${source_directory}
  make

  make -j9 VERBOSE=1 > tmp.txt 2>&1

  http://elinux.org/GCC_Tips
  gcc -E -dM - < /dev/null | cut -c 9- | sort #Print Pre-defined Macros
  g++ -E -x c++ - -v < /dev/null #include paths for g++
  gcc -M <file name> #list include file dep
  gcc -Wl,-y,printf hello.c #symbol trace
  gcc -Wl,-t <parameters> #See what Files the Linker is Using

  ld --verbose #linker infor (lib search path)
  ldconfig -v #all libraries

  getconf -a | grep libc #libc version

nfs example
-----------

::

  #server
  sudo apt-get install nfs-kernel-server nfs-common portmap
  sudo nano /etc/exports
  /home/pub 192.168.0.4(rw)
  sudo /etc/init.d/nfs-kernel-server restart
  sudo /etc/init.d/portmap restart
  sudo exportfs -a

  #client
  sudo mkdir /mnt/nfs
  sudo mount -t nfs 192.168.0.2:/home/pub /mnt/nfs
  sudo mount -o nolock -t nfs 192.168.0.2:/home/pub /mnt/nfs #if no portmap
  sudo umount /mnt/nf

misc commands
-------------

::

  du -sh dirName #directory size

  ExecStart=/usr/bin/strace -f -tt -o /run/%N.strace /lib/systemd/systemd-vconsole-setup

  sudo useradd -m -s /bin/bash -G gitusers somebody
  cat /etc/group|grep somebody
  cat /etc/passwd|grep  somebody
  sudo passwd 
  sync

  tr -c '\11\12\15\40-\176' 'X' < boot.svg > boot_clean.svg #remove not printabe


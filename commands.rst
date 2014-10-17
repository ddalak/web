Commands
========

Misc commands
-------------

::

  find -type l -exec rm -rf {} + #find delete all sym links

  du -sh dirName #directory size

  #get symbolic links
  find . -type l -exec ls -log --time-style=+ {} + | awk '{print $4" "$5" "$6}' > ~/system_links.txt


  ExecStart=/usr/bin/strace -f -tt -o /run/%N.strace /lib/systemd/systemd-vconsole-setup

  sudo useradd -m -s /bin/bash -G gitusers somebody
  cat /etc/group|grep somebody
  cat /etc/passwd|grep  somebody
  sudo passwd 
  sync

  tr -c '\11\12\15\40-\176' 'X' < boot.svg > boot_clean.svg #remove not printabe

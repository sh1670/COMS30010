# [Vagrant](https://www.vagrantup.com)-based VM configuration

<!--- -------------------------------------------------------------------- --->

- Install various pre-requisites, i.e.,

  - [VirtualBox](https://www.virtualbox.org)
    including any extension packs necessary, e.g., for USB device support,
    and
  - [Vagrant](https://www.vagrantup.com),
    plus associated plug-ins, as need be, via

    ```sh
    vagrant plugin install vagrant-disksize
    vagrant plugin install vagrant-reload
    ```

  Note that
  some features of the VM
  (e.g., access to USB devices)
  *may* demand you are a member of the
  [`vboxusers`](https://www.virtualbox.org/manual/ch02.html#install-linux-vboxusers);
  group; you can ensure this by executing

  ```sh
  sudo usermod --append --groups vboxusers ${USER}
  ```

- Launch the VM using *either* of the following approaches:

  1. Self-provisioned:

     - execute

       ```sh
       git clone --branch 2019 https://www.github.com/danpage/COMS30010.git ./COMS30010
       cd ./COMS30010/vagrant
       ```

       to 
       download
       a `Vagrantfile` 
       that references a
       bare [Ubuntu](https://app.vagrantup.com/ubuntu/boxes/bionic64)
       base box,

     - [edit](https://www.vagrantup.com/docs/vagrantfile) 
       the resulting `Vagrantfile` to suit any specific requirements,

     - execute 

       ```sh
       vagrant up
       ```

       after which the VM boots, and the provisioning step executes:
       this may take some time.

  2. Pre-provisioned:

     - execute

       ```sh
       mkdir --parents ./COMS30010/vagrant
       cd ./COMS30010/vagrant
       vagrant init danpage/COMS30010
       ```

       to 
       generate
       a `Vagrantfile`
       that references a
       [pre-provisioned](https://app.vagrantup.com/danpage/boxes/COMS30010)
       base box,

     - [edit](https://www.vagrantup.com/docs/vagrantfile) 
       the resulting `Vagrantfile` to suit any specific requirements,
       e.g., enable X11 forwarding by adding the lines

       ```
       config.ssh.forward_agent = true
       config.ssh.forward_x11   = true
       ```

     - execute

       ```sh
       vagrant up
       ```

       after which the VM boots:
       this may take some time.

- Access the VM 
  by executing

  ```sh
  vagrant ssh
  ```

  noting that

  - `/home/vagrant/COMS30010`
    will house
    relevant teaching material *pre-downloaded* during the provisioning step,
    and
  - `/home/vagrant/share`
    will represent
    a 
    [shared folder](https://www.virtualbox.org/manual/ch04.html#sharedfolders), 
    allowing transfer of data to and from the host and guest.

<!--- -------------------------------------------------------------------- --->

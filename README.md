# TMCB150_config
ipyparallel configuration files to perform distributed and parallel computing in the ACME computer lab.

### Configuration Steps (for future students)
1. Run `ipython profile create --parallel --profile=<NETID>`
- Create a new git repository. Name it whatever you want.
- Create a new directory `mkdir ~/myacmeshare/ipyparallel_config`
- Clone your new git repository into the directory you just created.
- Run `ipcontroller --profile=<NETID> --ip=<IPADDRESS>` to start the controller. This will also create the necessary JSON files. You can find out what your IP address is by running `ifconfig`.
- Open a new terminal and copy the file `~/.ipython/profile_<NETID>/security/ipcontroller-engine.json` to your new git repository folder.
- On the remote machine, run `ipython profile create --parallel --profile=<NETID>` and edit `~/.ipython/profile_<NETID>/ipengine_config.py`. Uncomment the line `c.IPEngineApp.url_file = u''` and include the path to your `ipcontroller-engine.json` file. For example, the line in my config looks like:
```
c.IPEngineApp.url_file = u'/home/tkchris@byu.local/myacmeshare/ipyparallel_config/TMCB150_config/ipcontroller-engine.json'
```
- To ensure that your configuration has worked correctly, (with your controller still running), on the remote machine run `ipengine --profile=<NETID>`. This will start one engine, and you should see it register in your terminal with your controller running. If you don't see anything happen, then that means something isn't correct.
- NOTE: You can repeat step 7 on as many machines as you want. In theory, you could harness the resources of the entire lab, but please be considerate of others.

### Running ipython cluster after it has been configured
1. Start the controller by running `ipcontroller --reuse --profile=<NETID> --ip=<IPADDRESS>`. The `--reuse` is essential because you will have to redo lots of the configuration if you don't include this. If your IP address has changed since you configured your computer, that means that you will have to redo the configuration. It is much easier to configure the second time around once you know what you are doing.
- SSH into the remote machine and run (this works if you want to start engines locally too) `ipcluster engines --n <NUM OF ENGINES> --profile=<NETID>`. It is best practice to not start more engines than there are cores on the computer. There are 8 cores on the desktops in the lab. Keep in mind you don't want to completely monopolize the resources of the computer, so be considerate of other users.

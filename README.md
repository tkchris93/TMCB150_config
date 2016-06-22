# TMCB150_config
ipyparallel configuration files to perform distributed and parallel computing in the ACME computer lab.

### Configuration Steps (for future guide)
- Run `ipython profile create --parallel --profile=tkchris`
- Create a new git repository. Name it whatever you want.
- Create a new directory `mkdir ~/myacmeshare/ipyparallel_config`
- Clone your new git repository into the directory you just created.
- Run 'ipcontroller --profile=tkchris' to start the controller. This will also create the necessary JSON files. 
- Open a new terminal and copy the file `~/.ipython/profile-<NETID>/security/ipcontroller-client.json` to your new git repository folder.

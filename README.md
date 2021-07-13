# c language notebook

time: 2021-7-13 21:01:07

## basic

install emacs, vagrant, virtualbox

## emacs config

```bash
mkdir -p ~/.emacs.d
cd ~/.emacs.d
touch init.el
```

write content:

```elisp
;; xxx~ file save to ~/.emacs.d/.saves directory
(setq backup-directory-alist `(("." . "~/.emacs.d/.saves")))
```

## vagrant and virtualbox

import vm image:

```bash
vagrant box add ubuntu/xenial64 /d/vtest/images/xenial-server-cloudimg-amd64-vagrant.box
```

fix mount VirtualBox shared folders issue, install vagrant vbguest plugins

```bash
vagrant plugin install vagrant-vbguest --plugin-clean-sources --plugin-source https://gems.ruby-china.com/
```

manual install/update VBox Guest Additions: 

```ruby
config.vbguest.auto_update = false
```

exec command:
```bash
vagrant up
vagrant vbguest
```

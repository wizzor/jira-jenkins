# Eficode Jira-ZAP-Jenkins Tutorial

This repository is intended to be used with [this blog post](https://eficode.com/blog/some/path). It is a combination of two services (Jira and Jenkins) built into a single Vagrantfile, to create a network between them.

The tutorial contains instructions on how set up security threat management system based on Jira and Zed Attack Proxy over Jenkins. A video is available [here](http://youtube.com/example)

## Jira

The Jira installation script is based on Atlassian's own Jira installation Vagrantfile available [here](https://bitbucket.org/atlassian/jira-box/downloads/Vagrantfile), but which unfortunately did not work.

## Jenkins
The Jenkins related parts are an adaptation of [balamaci/jenkins-ansible](https://github.com/balamaci/jenkins-ansible) repository.
#!/usr/bin/env groovy
def jenkinsfile

def overrides = [
    scriptVersion           : 'v7',
    pipelineScript          : 'https://git.aurora.skead.no/scm/ao/aurora-pipeline-scripts.git',
    versionStrategy         : [
      [ branch : 'master', versionHint:'1' ]
    ],
    iqOrganizationName      : "Team Sirius IO",
    iqCredentialsId         : "ioteam-iq",
    iqBreakOnUnstable       : false,
    publishToNpm            : false,
    deployToNexus           : false,
    openShiftBuild          : false,
    nideVersion             : "12",


    github                 : [
      enabled              : true,
      push                 : env.BRANCH_NAME == "master",
      repoUrl              : "https://github.com/Skatteetaten/skattemeldingen",
    ]

]

fileLoader.withGit(overrides.pipelineScript, overrides.scriptVersion) {
   jenkinsfile = fileLoader.load('templates/webleveransepakke')
}
jenkinsfile.run(overrides.scriptVersion, overrides)
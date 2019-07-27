node("linux") {
  stage("git pull") {
    checkout scm
  }
  stage("parameters") {
    properties([
      parameters([
        choice(
          name: "deploy",
          description: "Enable or disable deploy step.",
          choices: ["enabled", "disabled"]
        )
      ])
    ])
  }
  stage("deploy") {
    if (params.deploy == "enabled") {
      build job: "devops-deploy-python"
    } else {
      echo "Deploy is disabled. Skipping deployment"
    }
  }
}

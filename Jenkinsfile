import groovy.json.JsonSlurperClassic

@NonCPS
def jsonParse(def json) {
    new groovy.json.JsonSlurperClassic().parseText(json);
}

node {
        if(env.RELEASE_TAG) {
            checkout scm: [$class: 'GitSCM', branches: [[name: "refs/tags/${env.RELEASE_TAG}"]]], poll: false
        }
            else {
                checkout scm
        }
    def packageJson =  jsonParse(readFile("package.json"))
    println(packageJson.name);
}

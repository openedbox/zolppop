## 集中配置服务 Config-Server

相关环境变量如下:
# env APP_PROFILE native or git
# when APP_PROFILE is native
# env APP_CONFIG_NATIVE_REPO_DIR for config file location, pls mount host dir and point it
# when APP_PROFILE is git
# env APP_CONFIG_GIT_REPO_URL for git url
# env APP_CONFIG_GIT_REPO_BASEDIR for base dir
# env APP_CONFIG_GIT_REPO_USERNAME for login user name
# env ${APP_CONFIG_GIT_REPO_PASSWORD for login password
# env ${APP_CONFIG_GIT_REPO_SEARCHPATH for search path
# env ${APP_CONFIG_GIT_REPO_FORCEPULL for load configration when service startup whether or not,default true 
# env ${APP_CONFIG_GIT_REPO_SSLVALIDATION:true} for ssl validation when git connect. default true

# env CONSUL_HOST consul server setting
# env CONSUL_PORT consol port setting

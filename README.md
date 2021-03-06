# AppVeyor Cookbook

This cookbook
- Installs the [AppVeyor deployment agent](https://www.appveyor.com/docs/deployment/agent#installing-appveyor-deployment-agent)
- [Triggers a deployment](https://www.appveyor.com/docs/api/environments-deployments#start-deployment) from the Appveyor API

It does not install IIS or any other related services.

## Requirements
### Chef
- Chef 12.5+

## Platform
- Windows

## Recipes
### default  
Installs the AppVeyor agent

Set the following attributes:
```
node['environment_access_key']
node['deployment_group']
```

For more examples see the test/fixtures directory 
## Resources
### Agent Install
```ruby
appveyor_agent '3.12.0' do
  environment_access_key '1234abcd890432kj'
  deployment_group 'test'
end
```

### Deploy
`appveyor_deploy` start the deployment for the specified environment in AppVeyor
```ruby
appveyor_deploy '1.0.269' do
  api_token node['api_token']
  environment_name 'development'
  project_slug 'project-X'
  account_name 'my-account'
end
```

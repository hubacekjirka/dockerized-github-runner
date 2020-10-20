<h1 align="center">Welcome to the dockerized github runner repo 👋</h1>
<p>
  <a href="https://twitter.com/hubacekjirka">
    <img alt="Twitter: hubacekjirka" src="https://img.shields.io/twitter/follow/hubacekjirka.svg?style=social" target="_blank" />
  </a>
</p>

### 🏠 [Homepage](http://blog.hubacek.uk)

> The repo contains a dockerized GitHub runner for Action's execution. It's suitable for people who have specific requirements
on the runner configuration or their project outgrew Github's hosted runner capacity. 
The repository considers only x64 architecture, but the same principle should work with other architectures as well.

> The runner automatically registers itself when it starts. After it's finished the configuration, it waits for tasks from Github.
On its graceful shutdown (*docker stop* command), it deregisters itself from Github.

> The runner can communicate with the host's Docker for executing *docker* commands.

## Usage

### Docker Build
The building process performs the following tasks:
- retrieves and extracts the runner
- retrieves and setup Docker CLI
- creates actions use
- sets permissions
- sets the entry point which serves as the runner's wrapper.

```sh
docker build -t hubacekjirka/github_runner_x64 -f ./github_runner.dockerfile .
```

### Running container
Before running the container, make sure you've got:
- personal token with admin privileges on the repo set
- .env_github_runner_x64 environment file set.

*-v /var/run/docker.sock:/var/run/docker.sock * open socket with host.

#### Interactive
```sh
docker run -it -v /var/run/docker.sock:/var/run/docker.sock --env-file .env_github_runner_x64 hubacekjirka/github_runner_x64
```

#### Detached
```sh
docker run -d -v /var/run/docker.sock:/var/run/docker.sock --env-file .env_github_runner_x64 hubacekjirka/github_runner_x64
```

### Result
If everything worked well, one should see the runner in the runner list:

<img src="https://github.com/hubacekjirka/dockerized-github-runner/blob/main/result.jpg?raw=true" width="50%" height="50%"/>


## Author

👤 **jiri hubacek**

* Twitter: [@hubacekjirka](https://twitter.com/hubacekjirka)
* Github: [@hubacekjirka](https://github.com/hubacekjirka)

## Credits
* kefranabg: [Readme generator](https://github.com/kefranabg/readme-md-generator)
* John Bohannonn: [GitHub Actions self-hosted runners on Google Cloud](https://github.blog/2020-08-04-github-actions-self-hosted-runners-on-google-cloud/)
* Jérôme Petazzoni: [Using Docker-in-Docker for your CI or testing environment? Think twice.](https://jpetazzo.github.io/2015/09/03/do-not-use-docker-in-docker-for-ci/)

## Show your support

Give a ⭐️ if this project helped you!

## 📝 License

Copyright © 2020 [jiri hubacek](https://github.com/hubacekjirka).<br />
This project is [MIT](https://github.com/hubacekjirka/dockerized-github-runner/blob/master/LICENSE) licensed.

***
_This README was generated with ❤️ by [readme-md-generator](https://github.com/kefranabg/readme-md-generator)_

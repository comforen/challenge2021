# ComForEn Self-optimization Challenge

Welcome to supplement repository for this year's challenge.

## What is this repository about?

The instructions and virtual environment for solving the *Self-optimization Challenge 2021*, in a European Energy Community setting, are available in this repository. Participants are invited to join and submit their solutions in order to solve this challenge. A prize will be given to the winner. In addition, an expert panel would be available for feedback and mentoring following the conference.

More details about the conference and the challenge are available at the conference [website](http://www.comforen.org).

## How to run the virtual environment?

The virtual-environment is composed with Docker. Therefore, you will need Docker and compose already installed.

To run the environment:

1. Clone this repository.
2. In a shell, navigate to the `pre` folder in the cloned repository.
3. You can run the stack with either `docker compose` or `docker-compose` commands
    * To run in an interactive mode, execute `docker-compose up` or `docker compose up`
    * To run it in the detached mode execute `docker-compose up -d` or `docker compose up -d`
4. You can access the running monitoring toolkit [Prometheus](https://prometheus.io/docs/introduction/overview/)  and [Grafa](https://grafana.com/) dashboard with
    * [http://localhost:9099](http://localhost:9099) for Promethus console
    * [http://localhost:3030](http://localhost:3030) for Grafa console (username: `admin`, password: `admin`)
    * In Grafa, there should a dashboard named `ComForEn 2021 Challenge Demo` in the `Services` [folder](http://localhost:3030/dashboards) that you can open and view the values.
5. Stop the stack by executing either of these commands
    * `docker-compose down` will stop as well as remove all the containers
    * `docker-compose down -v` would additionally clear the volumes

## How to submit your solved challenge?

Please see conference [homepage](http://www.comforen.org).

## Conference information

![ComForEn 2021](http://www.comforen.org/.cm4all/mediadb/ComForEn_2021%20Logo.jpg)

On 22. and 23. November 2021 in Vienna and online

For more information and registration, please visit the conference [homepage](http://www.comforen.org).

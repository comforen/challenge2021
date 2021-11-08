# ComForEn Self-optimization Challenge

Welcome to supplement repository for this year's challenge.

## What is this repository about?

The instructions and virtual environment for solving the *Self-optimization Challenge 2021*, in a European Energy Community setting, are available in this repository. Participants are invited to join and submit their solutions in order to solve this challenge. A prize will be given to the winner. In addition, an expert panel would be available for feedback and mentoring following the conference.

More details about the conference and the challenge are available at the conference [website](http://www.comforen.org).

## Composition and interaction
The environment is composed of the following componets in addition to dashboard and monitoring toolkit.

|           Component            |   Type   | # of instances | 
| ------------------------------ | -------- | -------------- |
| Residential with generation    | CUSTOMER | 2              |
| Residential without generation | CUSTOMER | 2              |
| Commercial with generation     | CUSTOMER | 1              |
| Commercial with generation     | CUSTOMER | 1              |
| Community PV                   | CPV      | 1              |
| Community Battery              | CBATTERY | 1              |
| Price/Market Manager           | PRICE    | 1              |


### Customer
REST Endpoints

|      Endpoint       | Method | Input |                 Sample Output                 |
| ------------------- | ------ | ----- | --------------------------------------------- |
| `host:8080/measure` | GET    |       | `{"active_power":3.93,"reactive_power":0.47}` |

### Community PV
|      Endpoint       | Method | Input |                 Sample Output                 |
| ------------------- | ------ | ----- | --------------------------------------------- |
| `host:8080/measure` | GET    |       | `{"active_power":3.93,"reactive_power":0.47}` |

### Community Battery
|      Endpoint       | Method |                     Input                     |                 Sample Output                 |
| ------------------- | ------ | --------------------------------------------- | --------------------------------------------- |
| `host:8080/config`  | POST   | `{"active_power":3.93,"reactive_power":0.47}` | `{"active_power":3.93,"reactive_power":0.47}` |
| `host:8080/measure` | GET    |                                               | `{"active_power":3.93,"reactive_power":0.47}` |

## Price Manager

|      Endpoint       | Method | Input |                                                           Sample Output                                                           |
| ------------------- | ------ | ----- | --------------------------------------------------------------------------------------------------------------------------------- |
| `host:8080/info` | GET    |       | `{"gridSelling": 0, "gridBuying": 0, "p2pSelling": 0, "p2pBuying": 0, "cBatterySelling": 0, "cBatteryBuying": 0, "cPVBuying": 0}` |


## How to run the virtual environment?

The virtual-environment is composed with Docker. Therefore, you will need Docker and compose already installed.

To run the environment:

1. Clone this repository.
2. In a shell, navigate to the `pre` folder in the cloned repository and execute one of the following
1. You can run the stack with either `docker compose` or `docker-compose` commands
    * To run in an interactive mode, execute `docker-compose up` or `docker compose up`
    * To run it in the detached mode execute `docker-compose up -d` or `docker compose up -d`
4. You can access the running monoting toolkit [Prometheus](https://prometheus.io/docs/introduction/overview/)  and [Grafa](https://grafana.com/) dashboard with
    * [http://localhost:9099](http://localhost:9099) for Promethus console
    * [http://localhost:3030](http://localhost:3030) for Grafa console (username: `admin`, password: `admin`)
3. Stop the stack by executing either of these commands
    * `docker-compose down` will stop as well as remove all the containers
    * `docker-compose down --rmi all --volumes` will stop and remove all containers and clear the volums

## How to submit your solved challenge?

Please see conference [homepage](http://www.comforen.org).

## Conference information

![ComForEn 2021](http://www.comforen.org/.cm4all/mediadb/ComForEn_2021%20Logo.jpg)

On 22. and 23. November 2021 in Vienna and online

For more information and registration, please visit the conference [homepage](http://www.comforen.org).


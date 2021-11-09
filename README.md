# ComForEn Self-optimization Challenge

Welcome to supplement repository for this year's challenge.

## What is this repository about?

The instructions and virtual environment for solving the *Self-optimization Challenge 2021*, in a European Energy Community setting, are available in this repository. Participants are invited to join and submit their solutions in order to solve this challenge. A prize will be given to the winner. In addition, an expert panel would be available for feedback and mentoring following the conference.

More details about the conference and the challenge are available at the conference [website](http://www.comforen.org).

## Composition and interaction

The environment is composed of the following components in addition to dashboard and monitoring toolkit.

|                Component                |   Type   | # of instances |
| --------------------------------------- | -------- | -------------- |
| Residential Customer with generation    | CUSTOMER | 2              |
| Residential Customer without generation | CUSTOMER | 2              |
| Commercial Customer without generation     | CUSTOMER | 1              |
| Commercial Customer with generation     | CUSTOMER | 1              |
| Community PV                            | CPV      | 1              |
| Community Battery                       | CBATTERY | 1              |
| Price/Market Manager                    | PRICE    | 1              |

Each of these components provide a RESTful API with to perform the expected functions. Below you can find a summary of the REST API endpoints that you can use in your solution when solving the challenge. Please note that the environment in this repo is based on the mockups mostly that serve random values under the defined range in the datamodel. More detailed documentation along with client SDKs will be available soon.

### Customer

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
| `host:8080/measure` | GET    |       | `{"gridSelling": 0, "gridBuying": 0, "p2pSelling": 0, "p2pBuying": 0, "cBatterySelling": 0, "cBatteryBuying": 0, "cPVBuying": 0}` |

## How to run the virtual environment?

The virtual-environment is composed with Docker. Therefore, you will need Docker and compose already installed.

To run the environment:

1. Clone this repository.
2. Open a shell and navigate to the `pre` folder in the cloned repository.
3. You can run the stack with either `docker compose` or `docker-compose` commands
    * To run in an interactive mode, execute `docker-compose up` or `docker compose up`
    * To run it in the detached mode execute `docker-compose up -d` or `docker compose up -d`
4. You can access the running monitoring toolkit [Prometheus](https://prometheus.io/docs/introduction/overview/)  and [Grafa](https://grafana.com/) dashboard with
    * [http://localhost:9099](http://localhost:9099) for Promethus console
    * [http://localhost:3030](http://localhost:3030) for Grafa console (username: `admin`, password: `admin`)
    * After logging into Grafa, you can access the dashboard named `ComForEn 2021 Challenge Demo` from [http://localhost:3030/dashboards](http://localhost:3030/dashboards).
    ![Dashboard-sample](https://github.com/comforen/challenge2021/blob/main/docs/dashboard-sample.png)
5. Stop the stack by executing either of these commands
    * `docker-compose down` will stop as well as remove all the containers
    * `docker-compose down -v` additionally will clean the volumes

## How to submit your solved challenge?

Please see conference [homepage](http://www.comforen.org).

## What are the constraints and requirements for the developed solution?

Please see conference [homepage](http://www.comforen.org).

## Conference information

![ComForEn 2021](http://www.comforen.org/.cm4all/mediadb/ComForEn_2021%20Logo.jpg)

On 22. and 23. November 2021 in Vienna and online

For more information and registration, please visit the conference [homepage](http://www.comforen.org).


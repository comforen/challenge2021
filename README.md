# ComForEn Self-optimization Challenge

Welcome to supplement repository for this year's challenge.

**Table of Contents**
  * [What is this repository about?](#what-is-this-repository-about)
  * [Composition and interaction](#composition-and-interaction)
    + [Customer](#customer)
    + [Community PV](#community-pv)
    + [Community Battery](#community-battery)
    + [Price Manager](#price-manager)
    + [Prometheus Measures to be exposed](#prometheus-measures-to-be-exposed)
    + [Community battery properties and constraints](#community-battery-properties-and-constraints)
  * [How to run the virtual environment?](#how-to-run-the-virtual-environment)
  * [How to submit your solved challenge and until when?](#how-to-submit-your-solved-challenge-and-until-when)
  * [What are the constraints and requirements for the developed solution?](#what-are-the-constraints-and-requirements-for-the-developed-solution)
  * [Conference information](#conference-information)

## What is this repository about?

The instructions and virtual environment for solving the *Self-optimization Challenge 2021*, in a European Energy Community setting, are available in this repository. Participants are invited to join and submit their solutions in order to solve this challenge. A prize will be given to the winner. In addition, an expert panel would be available for feedback and mentoring following the conference.

More details about the conference and the challenge are available at the conference [website](http://www.comforen.org).

## Composition and interaction

The environment is composed of the following components in addition to dashboard and monitoring toolkit.

|                Component                |   Type   | # of instances |
| --------------------------------------- | -------- | -------------- |
| Residential Customer with generation `rcwpv`    | CUSTOMER | 2              |
| Residential Customer without generation `rcwopv` | CUSTOMER | 2              |
| Commercial Customer without generation `ccwopv` | CUSTOMER | 1              |
| Commercial Customer with generation `ccwpv`     | CUSTOMER | 1              |
| Community PV `cpv`                           | CPV      | 1              |
| Community Battery `cbat`                       | CBATTERY | 1              |
| Price/Market Manager `price`                    | PRICE    | 1              |

To perform the expected functions, each of these components provides a RESTful API. The REST API endpoints that you can use in your solution when solving the challenge are listed below. Please keep in mind that the environment in this repo is mostly based on mockups that serve random values within the range defined in the data model. More information, as well as other resources, can be found at the accompanying [GitHub Pages](https://comforen.github.io/).

### Customer

|      Endpoint       | Method | Input |                 Sample Output                 |
| ------------------- | ------ | ----- | --------------------------------------------- |
| `host:8080/measure` | GET    |       | `{"active_power":3.93,"reactive_power":0.47}` |

### Community PV

|      Endpoint       | Method | Input |                 Sample Output                 |
| ------------------- | ------ | ----- | --------------------------------------------- |
| `cpv:8080/measure` | GET    |       | `{"active_power":3.93,"reactive_power":0.47}` |

### Community Battery

|      Endpoint       | Method |                     Input                     |                 Sample Output                 |
| ------------------- | ------ | --------------------------------------------- | --------------------------------------------- |
| `cbat:8080/config`  | POST   | `{"active_power":3.93,"reactive_power":0.47}` | |
| `cbat:8080/measure` | GET    |                                               | `{"active_power":3.93,"reactive_power":0.47}` |

### Price Manager

|      Endpoint       | Method | Input |                                                           Sample Output                                                           |
| ------------------- | ------ | ----- | --------------------------------------------------------------------------------------------------------------------------------- |
| `price:8080/info` | GET    |       | `{"gridSelling": 0, "gridBuying": 0, "p2pSelling": 0, "p2pBuying": 0, "cBatterySelling": 0, "cBatteryBuying": 0, "cPVBuying": 0}` |

### Prometheus Measures to be exposed

For each timestep, the optimization module has to expose the following measures for each of the six `<source>` in the environment. These sources are `rcwpv1`, `rcwpv2`, `rcwopv1`, `rcwopv2`, `ccwpv1` and `ccwopv1`. 


| Measure # | Measure |    Label(s)    |                                  Description                                   |
| --------- | ------- | -------------- | ------------------------------------------------------------------------------ |
| 1         | `fcpv`  | for=`<source>` | The amount of energy `used` by the `<source>` from the community PV            |
| 2         | `tcr`   | for=`<source>` | The amount of energy `shared` by the `<source>` to the residential customer(s) |
| 3         | `fcr`   | for=`<source>` | The amount of energy `used` by the `<source>` from the residential customer(s) |
| 4         | `tcc`   | for=`<source>` | The amount of energy `shared` by the `<source>` to the commercial customer(s)  |
| 5         | `fcc`   | for=`<source>` | The amount of energy `used` by the `<source>` from the commercial customer(s)  |
| 6         | `tcb`   | for=`<source>` | The amount of energy `shared` by the `<source>` to the community Battery       |
| 7         | `fcb`   | for=`<source>` | The amount of energy `used` by the `<source>` from the community Battery       |
| 8         | `tg`    | for=`<source>` | The amount of energy `shared` by the `<source>` to the grid                    |
| 9        | `fg`    | for=`<source>` | The amount of energy `used` by the `<source>` from the grid                    |

### Community battery properties and constraints

* The maximum capacity: **15kWh**
* The maximum charging/discharging power: **10kWh**
* If PV energy cannot be used by any customer, it will be fed into the grid and there will be **no direct transaction** from PV to battery.

## How to run the virtual environment?

The virtual-environment is composed with Docker. Therefore, you will need Docker and compose already installed.

To run the environment:

1. Clone this repository.
2. Open a shell and navigate to the `pre` folder in the cloned repository.
3. You can run the stack with either `docker compose` or `docker-compose` commands
    * To run in an interactive mode, execute `docker-compose up` or `docker compose up`
    * To run it in the detached mode execute `docker-compose up -d` or `docker compose up -d`
4. You can access the running monitoring toolkit [Prometheus](https://prometheus.io/docs/introduction/overview/)  and [Grafana](https://grafana.com/) dashboard with
    * [http://localhost:9099](http://localhost:9099) for Promethus console
    * [http://localhost:3030](http://localhost:3030) for Grafana console (username: `admin`, password: `admin`)
    * After logging into Grafana, you can access the dashboard named `ComForEn 2021 Challenge Demo` from [http://localhost:3030/dashboards](http://localhost:3030/dashboards).
    ![Dashboard-sample](https://github.com/comforen/challenge2021/blob/main/docs/dashboard-sample.png)
5. Stop the stack by executing either of these commands
    * `docker-compose down` will stop as well as remove all the containers
    * `docker-compose down -v` additionally will clean the volumes

## How to submit your solved challenge and until when?

Submission deadline: **17.11.2021**

For submission details, please see conference [homepage](http://www.comforen.org).

## What are the constraints and requirements for the developed solution?

Please see conference [homepage](http://www.comforen.org).

## Conference information

![ComForEn 2021](http://www.comforen.org/.cm4all/mediadb/ComForEn_2021%20Logo.jpg)

On 22. and 23. November 2021 in Vienna and online

For more information and registration, please visit the conference [homepage](http://www.comforen.org).


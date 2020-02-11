# 3-ej-dif-int-mno-feb-2020
ejercicios a realizar en github classroom para nota de diferenciación e integración

Instrucciones:

1. Misma persona `Admin` que aceptó invitación a la tarea de github classroom pasada debe aceptar la invitación a esta tarea. Recuerden que sólo una persona integrante de cada equipo debe aceptar.

2. Invitar a sus integrantes de su equipo al **repo privado**. 

3. Resuelvan por equipos los ejercicios de programación de las notas de diferenciación e integración numérica:

[1.4.Polinomios_de_Taylor_y_diferenciacion_numerica.ipynb](1.4.Polinomios_de_Taylor_y_diferenciacion_numerica.ipynb) (nota escrita en jupyterlab + kernel de R)

[1.5.Integracion_numerica.ipynb](1.5.Integracion_numerica.ipynb) (nota escrita en jupyterlab)


¿Cómo puedo crear dos botones de binder que me lleven a ambientes distintos de `docker`?

1) En el `README.md` de su **repo privado** creen dos botones de [binder](https://mybinder.org/) que sean como el siguiente con ligeras modificaciones:

```
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/<mi user de github>/<mi repo público>/<mi rama para un dockerfile>?urlpath=lab) 
```

```
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/<mi user de github>/<mi repo público>/<mi rama para el otro dockerfile>?urlpath=lab) 
```

2) Observen que se están usando en los botones de binder **dos ramas distintas de su repo público**. Por esto, deben colocar en cada rama un sólo Dockerfile. Los `Dockerfile`'s que deben usar son los siguientes: 

Dockerfile para la nota 1.4:

```
FROM palmoreck/jupyterlab_r_kernel_binder:1.1.0
ARG NB_USER=jovyan
ARG NB_UID=1000
ENV USER ${NB_USER}
ENV NB_UID ${NB_UID}
ENV HOME /home/${NB_USER}
COPY . ${HOME}
USER root
RUN chown -R ${NB_UID} ${HOME}

USER ${NB_USER}
```

Dockerfile para la nota 1.5:

```
FROM palmoreck/jupyterlab_numerical_binder_test:1.1.0
ARG NB_USER=jovyan
ARG NB_UID=1000
ENV USER ${NB_USER}
ENV NB_UID ${NB_UID}
ENV HOME /home/${NB_USER}
COPY . ${HOME}
USER root
RUN chown -R ${NB_UID} ${HOME}

USER ${NB_USER}
```




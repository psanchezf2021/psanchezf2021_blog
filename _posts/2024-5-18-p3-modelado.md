---
layout: post
title: p3 modelado
---
Las tres primeras gráficas corresponden al escenario floor y las tres últimas al escenario sand.


![ruedas_floor](https://github.com/psanchezf2021/psanchezf2021_blog/assets/92941198/9fc9ad65-fcf8-4e03-8223-584291b4aabc)
![vel_pub_floor](https://github.com/psanchezf2021/psanchezf2021_blog/assets/92941198/af03a60d-0f37-437c-81e6-51ae2a806a9a)
![imu_floor](https://github.com/psanchezf2021/psanchezf2021_blog/assets/92941198/89c60d25-0962-4910-9d21-6e0a0b41dc49)
![wheels_sand](https://github.com/psanchezf2021/psanchezf2021_blog/assets/92941198/608b939e-7676-4ab6-b0e4-6eb34ecfcbed)
![pub_vel_sand](https://github.com/psanchezf2021/psanchezf2021_blog/assets/92941198/1861ac11-b0d1-4154-bc5a-28454fa79807)
![imu_sand](https://github.com/psanchezf2021/psanchezf2021_blog/assets/92941198/1fadb3ef-ec53-462d-881a-3a662589b9b2)

En la gráficas podemos observar como el comportamiento del rover es prácticamente idéntico.

Dos de las ruedas tienen velocidad positiva y dos negativa ya que están orientadas de manera opuesta.

Las velocidades publicadas en el topic son iguales a las descritas en el enunciado.

En la gráfica de aceleración del sensor imu podemos observar, casi al final un fragmento con forma de u, ahí es donde se está produciendo el choque.

[Video trayectoria floor](https://github.com/psanchezf2021/psanchezf2021_blog/assets/92941198/5da200f2-4434-4d71-a65c-5998f8d2bfc1)

[Video trayectoria sand](https://github.com/psanchezf2021/psanchezf2021_blog/assets/92941198/01a8ffe1-cbc1-41a5-9669-3023951ecfb0)

[Rosbag floor](https://github.com/psanchezf2021/psanchezf2021_blog/tree/master/grabacion_floor)

[Rosbag sand](https://github.com/psanchezf2021/psanchezf2021_blog/tree/master/grabacion_sand)

[Video parte a](https://github.com/psanchezf2021/psanchezf2021_blog/assets/92941198/273f2ac1-96b0-4985-966d-3ff062a50a9b)

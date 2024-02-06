---
layout: post
title: Zapremina 10-D sfere - Monte Carlo simulacija
date: 2024-02-06 17:39:00
description: Primjer Monte Carlo simulacije za procjenu zapremine sfere (Python)

---

# Izračunati zapreminu 10-D sfere
U ovom zadatku je potrebno izvršiti procjenu zapremine jedinične sfere u 10 dimenzionom prostoru koristeći Monte Carlo metod. Razmotrimo ekvivalentni problem u 2 dimenzije. Površina jediničnog kruga je data integralom:

$$I = \int \int_{+1}^{-1} f(x,y)dxdy,$$

gdje je $$ f(x,y)=1 $$  unutar kruga, a nula izvan:

$$ f(x,y)= 1 $$ ako je $$x^2 + y^2 ≤ 1$$, i $$0$$ za ostalo.

Površina kruga se može naći Monte Carlo integracijom: Generiramo skup N slučajnih tačaka (x,y), gdje su x i y u intervalu [0,1]; Izračunamo prethodni integtral koristeći odgovarajuću sumu:

$$ I \approx \frac{4}{N} \sum_{i=1}^N f(x_i,y_i).$$

Ovaj metod se može generalizirati na problem u 10-D prostoru.
Ako bismo problem riješavali na tradicionalni način (računanjem 10-D integrala), bilo bi potrebno mnogo više vremena: za npr. 100 tačaka (što ne bi dalo posebno dobar rezultat) duž svake ose, imali bismo $100^{10} = 10^{20}$ uzorkovanih tačaka, što je praktično "nemoguća misija" za bilo koji računar. Ali, korištenjem Monte Carlo metoda, moguće je dobiti zadovoljavajući rezultat i sa otprilike milion tačaka.

hint: https://en.wikipedia.org/wiki/Volume_of_an_n-ball


{% highlight python %}
# 2 D problem
import numpy as np
import random as r
x=[]
y=[]
N = 10000 #broj tacaka

#generirajmo x i y u prvom kvadrantu [0,1]
x = [r.random() for i in range(N)]
y = [r.random() for i in range(N)]

N_in = 0 #broj tacaka unutar kruga

for i in range(N):
    r = x[i]**2 + y[i]**2 
    if r <= 1:
        N_in += 1
        
I = 4*N_in/N  #4 kvadranta

print('Površina jediničnog kruga je ≈ ', I)
print('Analitička vrijednost je = ', np.pi)
{% endhighlight %}

{% highlight python %}
import random as r
import numpy as np
# 3D problem
x=[]
y=[]
z=[]

N = 100000 #broj tacaka

x = [r.random() for i in range(N)]
y = [r.random() for i in range(N)]
z = [r.random() for i in range(N)]

N_in = 0 #broj tacaka unutar kruga

for i in range(N):
    r = x[i]**2 + y[i]**2 + z[i]**2
    if r <= 1:
        N_in += 1
        
I = 8*N_in/N  # 8 oktanta (2^3)

print('Površina jedinične 3-D sfere je ≈ ', I)
print('Analitička vrijednost je = ', 4*np.pi/3)
{% endhighlight %}


{% highlight python %}
import random as r
import numpy as np
# 10D problem
x = []
N = 500000 #broj tacaka

for j in range(10):
    xs =  [r.random() for i in range(N)]
    x.append(xs)

N_in = 0 #broj tacaka unutar kruga

for i in range(N):
    r = 0
    for j in range(10):
        r += x[j][i]**2
    if r <= 1:
        N_in += 1
        
I = 2**10 *N_in/N  #2^10 ortanta

print('Površina jediničnog 10-D sfere je = ', I)
print('Analitička vrijednost je ≈ ', 2.55)
{% endhighlight %}


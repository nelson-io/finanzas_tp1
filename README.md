    library(knitr)
    library(tidyverse)

    ## -- Attaching packages ---------------------------------------------------------------------------------------------------------------- tidyverse 1.3.0 --

    ## v ggplot2 3.3.2     v purrr   0.3.4
    ## v tibble  3.0.1     v dplyr   1.0.0
    ## v tidyr   1.1.0     v stringr 1.4.0
    ## v readr   1.3.1     v forcats 0.5.0

    ## -- Conflicts ------------------------------------------------------------------------------------------------------------------- tidyverse_conflicts() --
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

TP N°1 Finanzas
===============

1. Colegio Privado
------------------

Un colegio privado que por año cobra diez cuotas mensuales de $20.000
c/u, acepta $180.000 como prepago de todas las cuotas de un año al
inicio de diciembre del año anterior al de cursado de clases.
Normalmente las cuotas se pagarían a principio de mes desde marzo a
diciembre del año de cursado.

#### a) ¿Cuál es el rendimiento efectivo anual implícito en este descuento? (Es decir, con qué tipo de interés efectivo anual, ambas cantidades serían iguales).

Para resolver este problema, descontamos todos los flujos de fondos al
período febrero a una tasa de descuento r con la formula de Annuity tal
que al descontar 2 períodos adicionales para obtener el valor presente
neto al mes de diciembre podamos igualar este monto al pago de $180.000
y así despejar r. Resolvemos por simulación

    for(r in seq(0.014, .015, .00001)){
      print(paste0("r = ",r," NPV = ",((20000/r)*(1-(1/(1+r)^10)))/((1+r)^2)))
    }

    ## [1] "r = 0.014 NPV = 180339.78620162"
    ## [1] "r = 0.01401 NPV = 180326.652001034"
    ## [1] "r = 0.01402 NPV = 180313.519031059"
    ## [1] "r = 0.01403 NPV = 180300.387291564"
    ## [1] "r = 0.01404 NPV = 180287.256782412"
    ## [1] "r = 0.01405 NPV = 180274.127503462"
    ## [1] "r = 0.01406 NPV = 180260.999454583"
    ## [1] "r = 0.01407 NPV = 180247.872635635"
    ## [1] "r = 0.01408 NPV = 180234.747046484"
    ## [1] "r = 0.01409 NPV = 180221.622686989"
    ## [1] "r = 0.0141 NPV = 180208.499557019"
    ## [1] "r = 0.01411 NPV = 180195.377656435"
    ## [1] "r = 0.01412 NPV = 180182.256985098"
    ## [1] "r = 0.01413 NPV = 180169.137542878"
    ## [1] "r = 0.01414 NPV = 180156.019329634"
    ## [1] "r = 0.01415 NPV = 180142.902345231"
    ## [1] "r = 0.01416 NPV = 180129.78658953"
    ## [1] "r = 0.01417 NPV = 180116.672062399"
    ## [1] "r = 0.01418 NPV = 180103.558763699"
    ## [1] "r = 0.01419 NPV = 180090.446693292"
    ## [1] "r = 0.0142 NPV = 180077.335851047"
    ## [1] "r = 0.01421 NPV = 180064.226236825"
    ## [1] "r = 0.01422 NPV = 180051.117850487"
    ## [1] "r = 0.01423 NPV = 180038.010691901"
    ## [1] "r = 0.01424 NPV = 180024.904760929"
    ## [1] "r = 0.01425 NPV = 180011.800057436"
    ## [1] "r = 0.01426 NPV = 179998.696581281"
    ## [1] "r = 0.01427 NPV = 179985.594332335"
    ## [1] "r = 0.01428 NPV = 179972.493310458"
    ## [1] "r = 0.01429 NPV = 179959.393515511"
    ## [1] "r = 0.0143 NPV = 179946.294947365"
    ## [1] "r = 0.01431 NPV = 179933.197605879"
    ## [1] "r = 0.01432 NPV = 179920.101490918"
    ## [1] "r = 0.01433 NPV = 179907.006602344"
    ## [1] "r = 0.01434 NPV = 179893.912940025"
    ## [1] "r = 0.01435 NPV = 179880.820503823"
    ## [1] "r = 0.01436 NPV = 179867.7292936"
    ## [1] "r = 0.01437 NPV = 179854.639309223"
    ## [1] "r = 0.01438 NPV = 179841.550550556"
    ## [1] "r = 0.01439 NPV = 179828.463017459"
    ## [1] "r = 0.0144 NPV = 179815.376709802"
    ## [1] "r = 0.01441 NPV = 179802.291627445"
    ## [1] "r = 0.01442 NPV = 179789.207770254"
    ## [1] "r = 0.01443 NPV = 179776.12513809"
    ## [1] "r = 0.01444 NPV = 179763.043730821"
    ## [1] "r = 0.01445 NPV = 179749.96354831"
    ## [1] "r = 0.01446 NPV = 179736.884590418"
    ## [1] "r = 0.01447 NPV = 179723.806857015"
    ## [1] "r = 0.01448 NPV = 179710.730347962"
    ## [1] "r = 0.01449 NPV = 179697.65506312"
    ## [1] "r = 0.0145 NPV = 179684.58100236"
    ## [1] "r = 0.01451 NPV = 179671.508165542"
    ## [1] "r = 0.01452 NPV = 179658.436552532"
    ## [1] "r = 0.01453 NPV = 179645.36616319"
    ## [1] "r = 0.01454 NPV = 179632.296997387"
    ## [1] "r = 0.01455 NPV = 179619.229054983"
    ## [1] "r = 0.01456 NPV = 179606.162335841"
    ## [1] "r = 0.01457 NPV = 179593.096839831"
    ## [1] "r = 0.01458 NPV = 179580.032566813"
    ## [1] "r = 0.01459 NPV = 179566.969516653"
    ## [1] "r = 0.0146 NPV = 179553.907689212"
    ## [1] "r = 0.01461 NPV = 179540.84708436"
    ## [1] "r = 0.01462 NPV = 179527.787701959"
    ## [1] "r = 0.01463 NPV = 179514.72954187"
    ## [1] "r = 0.01464 NPV = 179501.672603963"
    ## [1] "r = 0.01465 NPV = 179488.616888101"
    ## [1] "r = 0.01466 NPV = 179475.562394144"
    ## [1] "r = 0.01467 NPV = 179462.509121963"
    ## [1] "r = 0.01468 NPV = 179449.45707142"
    ## [1] "r = 0.01469 NPV = 179436.406242379"
    ## [1] "r = 0.0147 NPV = 179423.356634702"
    ## [1] "r = 0.01471 NPV = 179410.30824826"
    ## [1] "r = 0.01472 NPV = 179397.261082913"
    ## [1] "r = 0.01473 NPV = 179384.215138524"
    ## [1] "r = 0.01474 NPV = 179371.170414963"
    ## [1] "r = 0.01475 NPV = 179358.126912092"
    ## [1] "r = 0.01476 NPV = 179345.084629775"
    ## [1] "r = 0.01477 NPV = 179332.043567876"
    ## [1] "r = 0.01478 NPV = 179319.003726262"
    ## [1] "r = 0.01479 NPV = 179305.965104798"
    ## [1] "r = 0.0148 NPV = 179292.927703345"
    ## [1] "r = 0.01481 NPV = 179279.891521772"
    ## [1] "r = 0.01482 NPV = 179266.856559942"
    ## [1] "r = 0.01483 NPV = 179253.822817717"
    ## [1] "r = 0.01484 NPV = 179240.790294968"
    ## [1] "r = 0.01485 NPV = 179227.758991556"
    ## [1] "r = 0.01486 NPV = 179214.728907346"
    ## [1] "r = 0.01487 NPV = 179201.700042201"
    ## [1] "r = 0.01488 NPV = 179188.672395991"
    ## [1] "r = 0.01489 NPV = 179175.645968577"
    ## [1] "r = 0.0149 NPV = 179162.620759823"
    ## [1] "r = 0.01491 NPV = 179149.596769598"
    ## [1] "r = 0.01492 NPV = 179136.573997765"
    ## [1] "r = 0.01493 NPV = 179123.552444188"
    ## [1] "r = 0.01494 NPV = 179110.532108731"
    ## [1] "r = 0.01495 NPV = 179097.512991263"
    ## [1] "r = 0.01496 NPV = 179084.495091646"
    ## [1] "r = 0.01497 NPV = 179071.478409744"
    ## [1] "r = 0.01498 NPV = 179058.462945425"
    ## [1] "r = 0.01499 NPV = 179045.448698554"
    ## [1] "r = 0.015 NPV = 179032.435668992"

obtenemos una tasa efectiva mensual de 0.01426 que ahora transformamos
en TEA

    TEA <- ((1+.01426)^12 - 1)
    print(paste0("TEA = ", round(TEA,4)*100, "%"))

    ## [1] "TEA = 18.52%"

#### b) ¿Y si aceptasen $160.000 como prepago del total de las matrículas?

Replicamos nuevamente

    for(r in seq(0.030, .031, .00001)){
      print(paste0("r = ",r," NPV = ",((20000/r)*(1-(1/(1+r)^10)))/((1+r)^2)))
    }

    ## [1] "r = 0.03 NPV = 160810.685960521"
    ## [1] "r = 0.03001 NPV = 160799.357133257"
    ## [1] "r = 0.03002 NPV = 160788.029338545"
    ## [1] "r = 0.03003 NPV = 160776.702576275"
    ## [1] "r = 0.03004 NPV = 160765.376846335"
    ## [1] "r = 0.03005 NPV = 160754.052148612"
    ## [1] "r = 0.03006 NPV = 160742.728482996"
    ## [1] "r = 0.03007 NPV = 160731.405849374"
    ## [1] "r = 0.03008 NPV = 160720.084247635"
    ## [1] "r = 0.03009 NPV = 160708.763677665"
    ## [1] "r = 0.0301 NPV = 160697.444139354"
    ## [1] "r = 0.03011 NPV = 160686.125632591"
    ## [1] "r = 0.03012 NPV = 160674.808157261"
    ## [1] "r = 0.03013 NPV = 160663.491713256"
    ## [1] "r = 0.03014 NPV = 160652.176300463"
    ## [1] "r = 0.03015 NPV = 160640.861918768"
    ## [1] "r = 0.03016 NPV = 160629.548568063"
    ## [1] "r = 0.03017 NPV = 160618.236248234"
    ## [1] "r = 0.03018 NPV = 160606.924959169"
    ## [1] "r = 0.03019 NPV = 160595.614700757"
    ## [1] "r = 0.0302 NPV = 160584.305472888"
    ## [1] "r = 0.03021 NPV = 160572.997275448"
    ## [1] "r = 0.03022 NPV = 160561.690108325"
    ## [1] "r = 0.03023 NPV = 160550.38397141"
    ## [1] "r = 0.03024 NPV = 160539.07886459"
    ## [1] "r = 0.03025 NPV = 160527.774787753"
    ## [1] "r = 0.03026 NPV = 160516.471740787"
    ## [1] "r = 0.03027 NPV = 160505.169723582"
    ## [1] "r = 0.03028 NPV = 160493.868736025"
    ## [1] "r = 0.03029 NPV = 160482.568778005"
    ## [1] "r = 0.0303 NPV = 160471.269849412"
    ## [1] "r = 0.03031 NPV = 160459.971950132"
    ## [1] "r = 0.03032 NPV = 160448.675080054"
    ## [1] "r = 0.03033 NPV = 160437.379239068"
    ## [1] "r = 0.03034 NPV = 160426.084427062"
    ## [1] "r = 0.03035 NPV = 160414.790643924"
    ## [1] "r = 0.03036 NPV = 160403.497889542"
    ## [1] "r = 0.03037 NPV = 160392.206163806"
    ## [1] "r = 0.03038 NPV = 160380.915466604"
    ## [1] "r = 0.03039 NPV = 160369.625797823"
    ## [1] "r = 0.0304 NPV = 160358.337157354"
    ## [1] "r = 0.03041 NPV = 160347.049545085"
    ## [1] "r = 0.03042 NPV = 160335.762960904"
    ## [1] "r = 0.03043 NPV = 160324.477404701"
    ## [1] "r = 0.03044 NPV = 160313.192876363"
    ## [1] "r = 0.03045 NPV = 160301.90937578"
    ## [1] "r = 0.03046 NPV = 160290.626902838"
    ## [1] "r = 0.03047 NPV = 160279.34545743"
    ## [1] "r = 0.03048 NPV = 160268.065039442"
    ## [1] "r = 0.03049 NPV = 160256.785648762"
    ## [1] "r = 0.0305 NPV = 160245.507285281"
    ## [1] "r = 0.03051 NPV = 160234.229948887"
    ## [1] "r = 0.03052 NPV = 160222.953639469"
    ## [1] "r = 0.03053 NPV = 160211.678356914"
    ## [1] "r = 0.03054 NPV = 160200.404101112"
    ## [1] "r = 0.03055 NPV = 160189.130871953"
    ## [1] "r = 0.03056 NPV = 160177.858669324"
    ## [1] "r = 0.03057 NPV = 160166.587493115"
    ## [1] "r = 0.03058 NPV = 160155.317343215"
    ## [1] "r = 0.03059 NPV = 160144.048219511"
    ## [1] "r = 0.0306 NPV = 160132.780121895"
    ## [1] "r = 0.03061 NPV = 160121.513050253"
    ## [1] "r = 0.03062 NPV = 160110.247004476"
    ## [1] "r = 0.03063 NPV = 160098.981984451"
    ## [1] "r = 0.03064 NPV = 160087.717990068"
    ## [1] "r = 0.03065 NPV = 160076.455021217"
    ## [1] "r = 0.03066 NPV = 160065.193077784"
    ## [1] "r = 0.03067 NPV = 160053.932159661"
    ## [1] "r = 0.03068 NPV = 160042.672266736"
    ## [1] "r = 0.03069 NPV = 160031.413398898"
    ## [1] "r = 0.0307 NPV = 160020.155556035"
    ## [1] "r = 0.03071 NPV = 160008.898738037"
    ## [1] "r = 0.03072 NPV = 159997.642944794"
    ## [1] "r = 0.03073 NPV = 159986.388176193"
    ## [1] "r = 0.03074 NPV = 159975.134432124"
    ## [1] "r = 0.03075 NPV = 159963.881712477"
    ## [1] "r = 0.03076 NPV = 159952.63001714"
    ## [1] "r = 0.03077 NPV = 159941.379346002"
    ## [1] "r = 0.03078 NPV = 159930.129698953"
    ## [1] "r = 0.03079 NPV = 159918.881075882"
    ## [1] "r = 0.0308 NPV = 159907.633476677"
    ## [1] "r = 0.03081 NPV = 159896.386901229"
    ## [1] "r = 0.03082 NPV = 159885.141349426"
    ## [1] "r = 0.03083 NPV = 159873.896821157"
    ## [1] "r = 0.03084 NPV = 159862.653316312"
    ## [1] "r = 0.03085 NPV = 159851.41083478"
    ## [1] "r = 0.03086 NPV = 159840.16937645"
    ## [1] "r = 0.03087 NPV = 159828.928941211"
    ## [1] "r = 0.03088 NPV = 159817.689528953"
    ## [1] "r = 0.03089 NPV = 159806.451139565"
    ## [1] "r = 0.0309 NPV = 159795.213772936"
    ## [1] "r = 0.03091 NPV = 159783.977428955"
    ## [1] "r = 0.03092 NPV = 159772.742107513"
    ## [1] "r = 0.03093 NPV = 159761.507808497"
    ## [1] "r = 0.03094 NPV = 159750.274531799"
    ## [1] "r = 0.03095 NPV = 159739.042277306"
    ## [1] "r = 0.03096 NPV = 159727.811044909"
    ## [1] "r = 0.03097 NPV = 159716.580834495"
    ## [1] "r = 0.03098 NPV = 159705.351645957"
    ## [1] "r = 0.03099 NPV = 159694.123479182"
    ## [1] "r = 0.031 NPV = 159682.896334059"

obtenemos una tasa efectiva mensual de 0.03072 que ahora transformamos
en TEA

    TEA <- ((1+0.03072)^12 - 1)
    print(paste0("TEA = ", round(TEA,4)*100, "%"))

    ## [1] "TEA = 43.78%"

#### c) Si la tasa efectiva anual para un depósito a plazo fijo inferior a un año fuese 12% anual, ¿cuánto sería la cantidad de dinero de la que hay que disponer en diciembre del año anterior para hacer 10 plazos fijos que estén justo calzados con cada cuota a pagar? Si Ud. no tiene problemas de liquidez, ¿le conviene o no le conviene la oferta del colegio?

Primero transformamos la TEA en TEM y después descontamos con la fórmula
de Annuity

TEA 12%

    TEM <- ((1+.12)^(1/12))-1
    print(paste0("TEM = ",round(TEM,4)*100, "%"))

    ## [1] "TEM = 0.95%"

Ahora aplicamos formula de anuity sobre los 10 periodos y descontamos 2
periodos adicionales para evaluar el NPV

    ((20000/.0095)*(1-(1/(1+.0095)^10)))/((1+.0095)^2)

    ## [1] 186377.2

El NPV es de $186377.2 que es superior a los 180000 ofrecidos por el
colegio, atento a que es un pago, resulta conveniente tomar la oferta
del colegio

2. Start up.
------------

Al cabo de 10 años de experiencia corporativa Cecilia decide emprender.
Para llevar a cabo su proyecto, necesita una inversión de USD 100 mil.
De acuerdo a los pronósticos de Cecilia, los cashflows futuros esperados
son de USD 50 mil en el año 1 y USD 100 mil en el año 2. Estima que,
para este nivel de riesgo, su costo de oportunidad es del 15%. Si bien
su idea original era hacer una primera ronda de inversión entre su
familia y amigos, considera que esto le llevaría más tiempo del que
dispone y decide ir a su banco y pedir un préstamo. Las condiciones del
préstamo son las siguientes: Capital: USD 100 mil Plazo: 2 años. Tasa:
x% anual capitalizable Intereses pagaderos junto con el capital al
vencimiento del préstamo (final del año 2)

#### a) Determine los flujos de fondos del banco y de la emprendedora como función de la tasa de interés del banco. Considere un rango de tasas del 12% al 24%.

simulamos para tasas entre 12% y 24% los flujos del banco y de la
inversora

    rendimientos <- data.frame()


    for(i in seq(.12,.24,.01)){
      
      iter_df = data.frame(
        tasa = paste0(i*100,"%"),
        banco_c0 = -100000,
        banco_c1 = 0,
        banco_c2 = 100000*((1+i)^2),
        emp_c0 = 0,
        emp_c1 = 50000,
        emp_c2 = 100000 - 100000*((1+i)^2)
      )
      
      rendimientos = rbind(rendimientos, iter_df)
      
    }

    rendimientos %>% kable()

<table>
<thead>
<tr class="header">
<th style="text-align: left;">tasa</th>
<th style="text-align: right;">banco_c0</th>
<th style="text-align: right;">banco_c1</th>
<th style="text-align: right;">banco_c2</th>
<th style="text-align: right;">emp_c0</th>
<th style="text-align: right;">emp_c1</th>
<th style="text-align: right;">emp_c2</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">12%</td>
<td style="text-align: right;">-1e+05</td>
<td style="text-align: right;">0</td>
<td style="text-align: right;">125440</td>
<td style="text-align: right;">0</td>
<td style="text-align: right;">50000</td>
<td style="text-align: right;">-25440</td>
</tr>
<tr class="even">
<td style="text-align: left;">13%</td>
<td style="text-align: right;">-1e+05</td>
<td style="text-align: right;">0</td>
<td style="text-align: right;">127690</td>
<td style="text-align: right;">0</td>
<td style="text-align: right;">50000</td>
<td style="text-align: right;">-27690</td>
</tr>
<tr class="odd">
<td style="text-align: left;">14%</td>
<td style="text-align: right;">-1e+05</td>
<td style="text-align: right;">0</td>
<td style="text-align: right;">129960</td>
<td style="text-align: right;">0</td>
<td style="text-align: right;">50000</td>
<td style="text-align: right;">-29960</td>
</tr>
<tr class="even">
<td style="text-align: left;">15%</td>
<td style="text-align: right;">-1e+05</td>
<td style="text-align: right;">0</td>
<td style="text-align: right;">132250</td>
<td style="text-align: right;">0</td>
<td style="text-align: right;">50000</td>
<td style="text-align: right;">-32250</td>
</tr>
<tr class="odd">
<td style="text-align: left;">16%</td>
<td style="text-align: right;">-1e+05</td>
<td style="text-align: right;">0</td>
<td style="text-align: right;">134560</td>
<td style="text-align: right;">0</td>
<td style="text-align: right;">50000</td>
<td style="text-align: right;">-34560</td>
</tr>
<tr class="even">
<td style="text-align: left;">17%</td>
<td style="text-align: right;">-1e+05</td>
<td style="text-align: right;">0</td>
<td style="text-align: right;">136890</td>
<td style="text-align: right;">0</td>
<td style="text-align: right;">50000</td>
<td style="text-align: right;">-36890</td>
</tr>
<tr class="odd">
<td style="text-align: left;">18%</td>
<td style="text-align: right;">-1e+05</td>
<td style="text-align: right;">0</td>
<td style="text-align: right;">139240</td>
<td style="text-align: right;">0</td>
<td style="text-align: right;">50000</td>
<td style="text-align: right;">-39240</td>
</tr>
<tr class="even">
<td style="text-align: left;">19%</td>
<td style="text-align: right;">-1e+05</td>
<td style="text-align: right;">0</td>
<td style="text-align: right;">141610</td>
<td style="text-align: right;">0</td>
<td style="text-align: right;">50000</td>
<td style="text-align: right;">-41610</td>
</tr>
<tr class="odd">
<td style="text-align: left;">20%</td>
<td style="text-align: right;">-1e+05</td>
<td style="text-align: right;">0</td>
<td style="text-align: right;">144000</td>
<td style="text-align: right;">0</td>
<td style="text-align: right;">50000</td>
<td style="text-align: right;">-44000</td>
</tr>
<tr class="even">
<td style="text-align: left;">21%</td>
<td style="text-align: right;">-1e+05</td>
<td style="text-align: right;">0</td>
<td style="text-align: right;">146410</td>
<td style="text-align: right;">0</td>
<td style="text-align: right;">50000</td>
<td style="text-align: right;">-46410</td>
</tr>
<tr class="odd">
<td style="text-align: left;">22%</td>
<td style="text-align: right;">-1e+05</td>
<td style="text-align: right;">0</td>
<td style="text-align: right;">148840</td>
<td style="text-align: right;">0</td>
<td style="text-align: right;">50000</td>
<td style="text-align: right;">-48840</td>
</tr>
<tr class="even">
<td style="text-align: left;">23%</td>
<td style="text-align: right;">-1e+05</td>
<td style="text-align: right;">0</td>
<td style="text-align: right;">151290</td>
<td style="text-align: right;">0</td>
<td style="text-align: right;">50000</td>
<td style="text-align: right;">-51290</td>
</tr>
<tr class="odd">
<td style="text-align: left;">24%</td>
<td style="text-align: right;">-1e+05</td>
<td style="text-align: right;">0</td>
<td style="text-align: right;">153760</td>
<td style="text-align: right;">0</td>
<td style="text-align: right;">50000</td>
<td style="text-align: right;">-53760</td>
</tr>
</tbody>
</table>

#### b) ¿Cuál es el VAN del proyecto? ¿Cuál es el VAN de Cecilia, como función de la tasa de interés bancaria? ¿A partir de qué costo de financiamiento deja de ser atractivo este negocio para Cecilia?

Partiendo de que el costo de oportunidad es del 15%, determinamos el
NPV(VAN) del proyecto

    npv <- -100000 + 50000/1.15 + 100000/(1.15^2)
    paste0("El VAN del proyecto es de: $", round(npv,2))

    ## [1] "El VAN del proyecto es de: $19092.63"

Para la segunda parte de la pregunta, especificamos el VAN del
emprendedor e igualamos a 0 (simulaction)

    van_emprendedor <- data.frame()

    for(r in seq(.12,.24,.01)){
      
      iter_df <- data.frame(
        tasa_bancaria = paste0(100*r,"%"),
        npv = 0 + 50000/1.15 + 100000/(1.15^2) - 100000*((1+r)^2)/(1.15^2) 
      )
      
      van_emprendedor = rbind(van_emprendedor, iter_df)

    }

    van_emprendedor %>% kable()

<table>
<thead>
<tr class="header">
<th style="text-align: left;">tasa_bancaria</th>
<th style="text-align: right;">npv</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">12%</td>
<td style="text-align: right;">24241.966</td>
</tr>
<tr class="even">
<td style="text-align: left;">13%</td>
<td style="text-align: right;">22540.643</td>
</tr>
<tr class="odd">
<td style="text-align: left;">14%</td>
<td style="text-align: right;">20824.197</td>
</tr>
<tr class="even">
<td style="text-align: left;">15%</td>
<td style="text-align: right;">19092.628</td>
</tr>
<tr class="odd">
<td style="text-align: left;">16%</td>
<td style="text-align: right;">17345.936</td>
</tr>
<tr class="even">
<td style="text-align: left;">17%</td>
<td style="text-align: right;">15584.121</td>
</tr>
<tr class="odd">
<td style="text-align: left;">18%</td>
<td style="text-align: right;">13807.183</td>
</tr>
<tr class="even">
<td style="text-align: left;">19%</td>
<td style="text-align: right;">12015.123</td>
</tr>
<tr class="odd">
<td style="text-align: left;">20%</td>
<td style="text-align: right;">10207.940</td>
</tr>
<tr class="even">
<td style="text-align: left;">21%</td>
<td style="text-align: right;">8385.633</td>
</tr>
<tr class="odd">
<td style="text-align: left;">22%</td>
<td style="text-align: right;">6548.204</td>
</tr>
<tr class="even">
<td style="text-align: left;">23%</td>
<td style="text-align: right;">4695.652</td>
</tr>
<tr class="odd">
<td style="text-align: left;">24%</td>
<td style="text-align: right;">2827.977</td>
</tr>
</tbody>
</table>

para las tasas indicadas al comienzo del ejercicio siempre conviene
realizar el proyecto

    van_emprendedor <- data.frame()

    for(r in seq(.25,.26,.0001)){
      
      iter_df <- data.frame(
        tasa_bancaria = paste0(100*r,"%"),
        npv = 0 + 50000/1.15 + 100000/(1.15^2) - 100000*((1+r)^2)/(1.15^2) 
      )
      
      van_emprendedor = rbind(van_emprendedor, iter_df)

    }

    van_emprendedor %>% kable()

<table>
<thead>
<tr class="header">
<th style="text-align: left;">tasa_bancaria</th>
<th style="text-align: right;">npv</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;">25%</td>
<td style="text-align: right;">945.179584</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.01%</td>
<td style="text-align: right;">926.275236</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.02%</td>
<td style="text-align: right;">907.369376</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.03%</td>
<td style="text-align: right;">888.462004</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.04%</td>
<td style="text-align: right;">869.553119</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.05%</td>
<td style="text-align: right;">850.642722</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.06%</td>
<td style="text-align: right;">831.730813</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.07%</td>
<td style="text-align: right;">812.817391</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.08%</td>
<td style="text-align: right;">793.902457</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.09%</td>
<td style="text-align: right;">774.986011</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.1%</td>
<td style="text-align: right;">756.068053</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.11%</td>
<td style="text-align: right;">737.148582</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.12%</td>
<td style="text-align: right;">718.227599</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.13%</td>
<td style="text-align: right;">699.305104</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.14%</td>
<td style="text-align: right;">680.381096</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.15%</td>
<td style="text-align: right;">661.455577</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.16%</td>
<td style="text-align: right;">642.528544</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.17%</td>
<td style="text-align: right;">623.600000</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.18%</td>
<td style="text-align: right;">604.669943</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.19%</td>
<td style="text-align: right;">585.738374</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.2%</td>
<td style="text-align: right;">566.805293</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.21%</td>
<td style="text-align: right;">547.870699</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.22%</td>
<td style="text-align: right;">528.934594</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.23%</td>
<td style="text-align: right;">509.996975</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.24%</td>
<td style="text-align: right;">491.057845</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.25%</td>
<td style="text-align: right;">472.117202</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.26%</td>
<td style="text-align: right;">453.175047</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.27%</td>
<td style="text-align: right;">434.231380</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.28%</td>
<td style="text-align: right;">415.286200</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.29%</td>
<td style="text-align: right;">396.339509</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.3%</td>
<td style="text-align: right;">377.391304</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.31%</td>
<td style="text-align: right;">358.441588</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.32%</td>
<td style="text-align: right;">339.490359</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.33%</td>
<td style="text-align: right;">320.537618</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.34%</td>
<td style="text-align: right;">301.583365</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.35%</td>
<td style="text-align: right;">282.627599</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.36%</td>
<td style="text-align: right;">263.670321</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.37%</td>
<td style="text-align: right;">244.711531</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.38%</td>
<td style="text-align: right;">225.751229</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.39%</td>
<td style="text-align: right;">206.789414</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.4%</td>
<td style="text-align: right;">187.826087</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.41%</td>
<td style="text-align: right;">168.861248</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.42%</td>
<td style="text-align: right;">149.894896</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.43%</td>
<td style="text-align: right;">130.927032</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.44%</td>
<td style="text-align: right;">111.957656</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.45%</td>
<td style="text-align: right;">92.986767</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.46%</td>
<td style="text-align: right;">74.014367</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.47%</td>
<td style="text-align: right;">55.040454</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.48%</td>
<td style="text-align: right;">36.065028</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.49%</td>
<td style="text-align: right;">17.088091</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.5%</td>
<td style="text-align: right;">-1.890359</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.51%</td>
<td style="text-align: right;">-20.870321</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.52%</td>
<td style="text-align: right;">-39.851796</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.53%</td>
<td style="text-align: right;">-58.834783</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.54%</td>
<td style="text-align: right;">-77.819282</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.55%</td>
<td style="text-align: right;">-96.805293</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.56%</td>
<td style="text-align: right;">-115.792817</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.57%</td>
<td style="text-align: right;">-134.781853</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.58%</td>
<td style="text-align: right;">-153.772401</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.59%</td>
<td style="text-align: right;">-172.764461</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.6%</td>
<td style="text-align: right;">-191.758034</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.61%</td>
<td style="text-align: right;">-210.753119</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.62%</td>
<td style="text-align: right;">-229.749716</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.63%</td>
<td style="text-align: right;">-248.747826</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.64%</td>
<td style="text-align: right;">-267.747448</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.65%</td>
<td style="text-align: right;">-286.748582</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.66%</td>
<td style="text-align: right;">-305.751229</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.67%</td>
<td style="text-align: right;">-324.755387</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.68%</td>
<td style="text-align: right;">-343.761059</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.69%</td>
<td style="text-align: right;">-362.768242</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.7%</td>
<td style="text-align: right;">-381.776938</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.71%</td>
<td style="text-align: right;">-400.787146</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.72%</td>
<td style="text-align: right;">-419.798866</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.73%</td>
<td style="text-align: right;">-438.812098</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.74%</td>
<td style="text-align: right;">-457.826843</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.75%</td>
<td style="text-align: right;">-476.843100</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.76%</td>
<td style="text-align: right;">-495.860870</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.77%</td>
<td style="text-align: right;">-514.880151</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.78%</td>
<td style="text-align: right;">-533.900945</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.79%</td>
<td style="text-align: right;">-552.923251</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.8%</td>
<td style="text-align: right;">-571.947070</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.81%</td>
<td style="text-align: right;">-590.972401</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.82%</td>
<td style="text-align: right;">-609.999244</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.83%</td>
<td style="text-align: right;">-629.027599</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.84%</td>
<td style="text-align: right;">-648.057467</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.85%</td>
<td style="text-align: right;">-667.088847</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.86%</td>
<td style="text-align: right;">-686.121739</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.87%</td>
<td style="text-align: right;">-705.156144</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.88%</td>
<td style="text-align: right;">-724.192061</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.89%</td>
<td style="text-align: right;">-743.229490</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.9%</td>
<td style="text-align: right;">-762.268431</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.91%</td>
<td style="text-align: right;">-781.308885</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.92%</td>
<td style="text-align: right;">-800.350851</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.93%</td>
<td style="text-align: right;">-819.394329</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.94%</td>
<td style="text-align: right;">-838.439320</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.95%</td>
<td style="text-align: right;">-857.485822</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.96%</td>
<td style="text-align: right;">-876.533837</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.97%</td>
<td style="text-align: right;">-895.583365</td>
</tr>
<tr class="odd">
<td style="text-align: left;">25.98%</td>
<td style="text-align: right;">-914.634404</td>
</tr>
<tr class="even">
<td style="text-align: left;">25.99%</td>
<td style="text-align: right;">-933.686956</td>
</tr>
<tr class="odd">
<td style="text-align: left;">26%</td>
<td style="text-align: right;">-952.741021</td>
</tr>
</tbody>
</table>

observamos que para una tasa bancaria del 25.5% Cecilia se encontraría
indiferente.

3. Fondo de inversión
---------------------

Un fondo de inversión evalúa comprar el Correo Argentino. De acuerdo a
las estimaciones de demanda, los analistas del fondo calculan que en el
primer año venderán 4.000.000 de envíos por mes y en el segundo año,
logrando una fuerte expansión en el área de servicio, podrá vender
6.000.000 envíos mensuales. Además, el fondo estima vender la empresa al
final del segundo año a su precio de venta inicial, más una valorización
real del 15% (esto es, luego de tomar en cuenta la inflación acumulada
hasta el momento de la venta). El precio promedio del envío hoy es de 60
pesos y la tasa de inflación para los años que vienen se estima en 2,5%
mensual. El fondo anticipa actualizar los precios de los envíos
mensualmente de acuerdo a la inflación realizada. Los costos totales son
el 75% de los ingresos operativos. Como inversión alternativa de riesgo
similar, el fondo podría invertir el dinero en bonos riesgosos, con un
rendimiento del 50% anual, con capitalización anual.

#### a) ¿Cuáles son los cashflows asociados a este proyecto de inversión?

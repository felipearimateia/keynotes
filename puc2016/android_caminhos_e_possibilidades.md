build-lists: true
autoscale: true
# **Android: caminhos e possibilidades**

###Felipe Arimatéia

![filtered](https://fscl01.fonpit.de/userfiles/6727621/image/2016/Nougat/AndroidPIT-Android-N-Nougat-2480.jpg)

---

## **Felipe Arimatéia (Ari)**

Mobile Developer desde de 2010, apaixonado por código e viciado em séries.

![fill](https://raw.githubusercontent.com/felipearimateia/keynotes/master/images/Twitter-48.png) @twiterdoari

![fill](https://raw.githubusercontent.com/felipearimateia/keynotes/master/images/Google%20Plus-48.png) +FelipeArimateia

![fill](https://raw.githubusercontent.com/felipearimateia/keynotes/master/images/GitHub-48.png) felipearimateia

![left](https://raw.githubusercontent.com/felipearimateia/keynotes/master/images/eu_android.jpg)


---

# Caminhos

![filtered](http://marcialuz.com/wp-content/uploads/2016/03/duplo-caminho.jpg)

---

## **História do Android (I)**


* Criado pela Android Inc. em 2003.
* Em 2005 foi comprada pela Google.
* E em 2007 acontece o lancamento do sistema operacional Android para dispositivos móveis.

---

## **História do Android (II)**

![left] (http://i.kinja-img.com/gawker-media/image/upload/s---gYXJekO--/17mbtx34r69zkjpg.jpg)

Em outubro de 2008 foi lançado o primeiro aparelho com Android, o HTC Dream.

Hoje o Android possui 12 versões, e a atual é o Nougat 7.0.

E está presente em 83% dos smartphones do mundo[^1].

[^1]: IDC - [Smartphone OS Market Share, 2015 Q2](http://www.idc.com/prodserv/smartphone-os-market-share.jsp)

---

## **Developer Android**

![left] (http://www.androidcentral.com/sites/androidcentral.com/files/styles/large/public/postimages/108579/stopwatch_0.jpg?itok=GiaBVjLT)

O que você precisa para se tornar um desenvolvedor Android:

- Android Studio
- Device Android
- E uma conta de developer para publicar sua aplicação.
- Força de vontade para aprender mais

---

## **Material Design**

É o manifesto do Google para padronizar o design das suas aplicações e melhorar a usabilidade em todas as plataformas.

O Material Design também estabelece padrões de ícones, cores, animações, tipografia e hierarquias.

<!-- ![left](/Users/felipets/Pictures/google_design.png) -->
![left autoplay mute](../videos/material_design.mp4)


---

# Dicas - Suporte a multiplas telas

- Declarar no AndroidManifest os tamanhos de tela que seu aplicativo suporta.
- Fornecer layouts baseados em resoluções.
- Fornecer resources conforme a densidade da tela.
- Trabalhar com dimens categorizados por densidade.

---

SYNTAX:

```xml
<supports-screens android:resizeable=["true"| "false"]
                  android:smallScreens=["true" | "false"]
                  android:normalScreens=["true" | "false"]
                  android:largeScreens=["true" | "false"]
                  android:xlargeScreens=["true" | "false"]
                  android:anyDensity=["true" | "false"]
                  android:requiresSmallestWidthDp="integer"
                  android:compatibleWidthLimitDp="integer"
                  android:largestWidthLimitDp="integer"/>
```

---

# Dicas - Tamanho do APK

- Utilizar SVG para diminuir a quantidade de imagens e tamanho do APK.
- Criar APK's para cada resolução de tela.
- Utilize ProGuard para encolher o tamanho do código fonte.
- Habilitar o shrink resources para discartar os arquivos não utilizados.

---

```gradle
android {
    ...
    buildTypes {
        release {
            shrinkResources true
            minifyEnabled true
            proguardFiles getDefaultProguardFile('proguard-android.txt'),
                    'proguard-rules.pro'
        }
    }
}
```

---

# Dicas - lint

O [lint](https://developer.android.com/studio/write/lint.html?hl=pt-br) é uma ferramenta integrada ao Android Studio para análise de código, podendo detectar problemas de:

- Usabilidade
- Segurança
- Acessibilidade
- Performance
- Problemas com internacionalização

---

![fit](https://raw.githubusercontent.com/felipearimateia/keynotes/master/puc2016/inspect_code.png)

---

## **Bibliotecas**

- **Retrofit 2** - para requisições HTTP
- **Butterknife** - injeção de view
- **Picasso ou Glide** - download, cache e gerenciamento de imagens
- **Calligraphy** - facilitar o uso de fontes customizadas
- **Stetho** - Bridge para debugar aplicação via Chrome desktop

---

## **Curso Online**

O Google possuiu uma parceiria com a [Udacity](https://www.udacity.com/courses/android) e oferece todos os cursos de Android gratuitamente.

![left](https://cdn-images-1.medium.com/max/800/1*JXxovKQ2BOEKF69GG46V7A.png)

---

## **Literatura**

![](https://cdn-images-1.medium.com/max/600/1*YnsfS8SQoLMTYF3fqtgviQ.jpeg)
![](https://cdn-images-1.medium.com/max/600/1*ZIITaOliAjWGkWWYaI-bcg.png)
![](https://cdn-images-1.medium.com/max/600/1*_P85sRXaL9qFjolTdYeJLg.jpeg)

---

## **Comunidades**

- **AndroidDevBr no Slack** - [http://slack.androiddevbr.org](http://slack.androiddevbr.org)

- **Google Developers Group** - [GDG BH](http://gdgbh.org/)

- **Stack Overflow** - [http://stackoverflow.com](http://stackoverflow.com/questions/tagged/android)

- **Google Plus** - [+AndroidDevelopers](https://plus.google.com/+AndroidDevelopers)

![](https://lh3.googleusercontent.com/-dn0KZur_gIc/VXDMpd-r-TI/AAAAAAAAGoE/_lAUnSJaPM4U3_K_CW3Bi1Vfk9QOlMtzwCL0B/s1000-fcrop64=1,00710000ffffffff/02_g%252B_2banner.png)

---

# Possibilidades

![filtered](http://www.namitec.org.br/imagens-site/FrankfurtAutobahn.jpg)

---

## **Android for Work**

- 250M devices com Android foram utilizados para negócios em 2014[^2]
- 175M pessoas usam seus devices Android como BYOD
- 75M são devices coporativos.
- Crie aplicaticos para conectar-se a sistemas como SAP, Google Apps for Work, IBM, etc.

[^2]: Valores obtidos em [Android Developers](https://developer.android.com/work/index.html).

---

## **IoT**

- Utilizar sensores como o de temperatura ambiente e mandar um comando para o Ar Condicionado.
- Integração com o [Brillo](https://developers.google.com/brillo/) sistema operacional para embarcados baseado no Android.
- Integração com Smart House.

---

## **Sala de estar**

- A TV perdeu a posição de 1º primeira tela, mas não deixou de ser útil.
- Com Android TV é possível expandir suas aplicações para a TV.
- Crie games e o smartphone vira o controle.

![left fit](https://www.android.com/static/img/tv/lessbrowsing.jpg)

---

## Valide suas ideias

- No primeiro trimestre de 2016, 92% do market share brasileiro de smartphones é Android[^3].
- Base de usuários maior.
- Custo inicial para desenvolver no Android é baixo.

[^3]: statista - [Market share operating systems smartphone sales in Brazil from 2013 to 2016](https://www.statista.com/statistics/245189/market-share-of-mobile-operating-systems-for-smartphone-sales-in-brazil/)

---

![](/Users/felipets/Pictures/android_question.jpg)

---

# Obrigado

![](https://raw.githubusercontent.com/felipearimateia/keynotes/master/images/android_meetup_bh.png)

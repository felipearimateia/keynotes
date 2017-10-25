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

Hoje o Android possui 12 versões, e a atual é o Nougat 7.x.

E está presente em 87% dos smartphones do mundo[^1].

[^1]: IDC - [Smartphone OS Market Share, 2016 Q3](http://www.idc.com/prodserv/smartphone-os-market-share.jsp)

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

![left autoplay mute](../videos/material_design.mp4)

<!-- ![left](/Users/felipets/Pictures/google_design.png) -->

---

## Dicas - Suporte a multiplas telas

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

## Dicas - Tamanho do APK

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

## Dicas - lint

O [lint](https://developer.android.com/studio/write/lint.html?hl=pt-br) é uma ferramenta integrada ao Android Studio para análise de código, podendo detectar problemas de:

- Usabilidade
- Segurança
- Acessibilidade
- Performance
- Problemas com internacionalização

---

![fit](https://raw.githubusercontent.com/felipearimateia/keynotes/master/puc2016/inspect_code.png)

---

## Dicas - Para não ser banido (I)

Caso o seu aplicativo não tenham como função principal realizar ligações utilize a action `ACTION_DIAL`, para redirecionar o usuário para o app de ligação.

---

## Dicas - Para não ser banido (II)

O mesmo vale para o envio de SMS, utilize a action `ACTION_VIEW` combinado com a URI `sms:<phone_number>`, e o usuário sera redirecionado para o app de SMS.

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

## **Google Play for Education**

- Uma loja especifica para aplicativos voltados a educação.
- Os aplicativos são moderados e recomendados por educadores.
- O Google da todo um suporte para que instituições possam realizar compras de forma diferenciadas.

---

## **IoT**

- Utilizando os sensores de temperatura do ambiente e infravermelho, você pode enviar comandos para o Ar Condicionado.
- Com o Android Things você pode utilizar os recursos do SDK e o Android Studio, para criar seu ecosistema de IoT.

---

## **Sala de estar**

- A TV perdeu a posição de 1º primeira tela, mas não deixou de ser útil.
- Com Android TV é possível expandir suas aplicações para a TV.
- Crie games e o smartphone vira o controle.

![left fit](https://www.android.com/static/img/tv/lessbrowsing.jpg)

---

## **Saúde**

- Aproveite as API's do Andrid Wear, e monitore dados como batimentos cardiacos do usuário.
- Infrome para ele quantas calorias perdeu no dia.
- Conecte dispositivos externos para calcular a glicose.

---

## **Valide suas ideias**

- No primeiro trimestre de 2016, 92% do market share brasileiro de smartphones é Android[^3].
- Custo inicial para desenvolver no Android é baixo.
- A base de usuários para teste é maior que em outras plataformas.

[^3]: statista - [Market share operating systems smartphone sales in Brazil from 2013 to 2016](https://www.statista.com/statistics/245189/market-share-of-mobile-operating-systems-for-smartphone-sales-in-brazil/)

---

![original](http://i-cdn.phonearena.com/images/articles/148664-thumb/android-h1.jpg)

---

# Obrigado

![](https://raw.githubusercontent.com/felipearimateia/keynotes/master/images/android_meetup_bh.png)

# Construindo layouts complexos com ConstraintLayout

###Felipe Arimatéia

![](https://lh5.googleusercontent.com/KdXdMjtYBNBGszIxUB7f0noGLiOzNuuOanSo9oBeAxMo8aP1rXG5vEhsyNVy3ePrKfHy1UF5cs_869Py-fhlejaXNlDZ8PV-yv3U4hOCj3lYODCOYX61sSQ1_HaFuaibzSRI9Z6O)

---

## **Felipe Arimatéia (Ari)**

Mobile Developer desde de 2010, apaixonado por código e viciado em séries.

![fill](https://raw.githubusercontent.com/felipearimateia/keynotes/master/images/Twitter-48.png) @twiterdoari

![fill](https://raw.githubusercontent.com/felipearimateia/keynotes/master/images/Google%20Plus-48.png) +FelipeArimateia

![fill](https://raw.githubusercontent.com/felipearimateia/keynotes/master/images/GitHub-48.png) felipearimateia

![left](https://raw.githubusercontent.com/felipearimateia/keynotes/master/images/eu_android.jpg)

---

## What's new?

Durante o Google I/O 2016 foi anunciado novas tools e libraries para elaboração de layouts.

O Android Studio ganhou um editor de layout baseado em constrantis e também foi criado um novo container chamado **ConstraintLayout**.

---

## Setting up

* Baixar o [Android Studio 2.2 RC](http://tools.android.com/download/studio/builds/2-2-rc)

* E adicionar a dependência para ConstraintLayout:


```gradle
	compile 'com.android.support.constraint:constraint-layout:1.0.0-alpha7'
```

---

# Constraint Layout
![](https://4.bp.blogspot.com/-YnNwiE9u7DA/Vz0tcyCiPvI/AAAAAAAADE8/WMFg_XfxNyQQ95yyAe31iMBVy5AI-f9HgCLcB/s1600/constraint_layout_capture.png)

---

## What's it?

**Constraint** é a descrição de como um elemento deve se posicionar na view em relação a outros elementos.

Mesmo sendo similar ao *RelativeLayout*, **ConstraintLayout** é mais flexível e foi criado para ser usado com o novo editor de layout.

---

## Types of constraints

**Side connection with the layout**

![inline 100%](https://cdn-images-1.medium.com/max/800/1*j6BHbmYLEYo90lm3e_LXmw.gif)

<!--![inline 100%](constraint_type_1.png)-->

Conectar as laterais de um elemento nas extremidates do ConstraintLayout.

---

## Types of constraints

**Side connection with a view**

![inline 100%](https://cdn-images-1.medium.com/max/800/1*gN5yRFJ_cQptB_Q6FZ2rdg.gif)

<!--![inline 100%](constraint_type_2.png)-->

Conectar a extremidade de uma view, na extremidade oposta de outra view.

---

## Types of constraints

**Side alignment with a view**

<!--![inline 100%](constraint_type_3.png)-->
![inline 100%](https://cdn-images-1.medium.com/max/800/1*ANKcv2SgnGoYLMu1BUvV-w.gif)

Alinhar uma das bordas da view na mesma borda de outra view.

---

## Types of constraints

**Baseline alignment with a view**

![inline 100%](https://lh3.googleusercontent.com/tw5GwfOQPgQMqfwWlK6TZjUq-Dyy-ULNAaaWiJ3kC_flhWkdjXzLvdvl2d9W3yHAnL8gNphIa0In0m62FNiDSmZ0cm3-_21tTiSmZFuNbD0SSYt6po634pGcyUFwFnquU6K_snOC)

Alinhar a baseline de uma view com a baseline de outra view.

---

# Editor

![](https://raw.githubusercontent.com/felipearimateia/keynotes/master/devfestne/editor.png)

---

# Auto-connect

![fill](https://raw.githubusercontent.com/felipearimateia/keynotes/master/devfestne/auto_connect.png) O editor calcula e define automaticamente as constraints.

![inline 100%](https://cdn-images-1.medium.com/max/800/1*QUY4Z9sGGU75xArVYyXssA.gif)

---

# Manual Constraints

É possível desativar o auto-connect e definir manulamente as contraints.

![inline 100%](https://cdn-images-1.medium.com/max/800/1*pY5ULqzEvctMZWFaCAc-yg.gif)

---

# Infer Constraints

![fill](https://raw.githubusercontent.com/felipearimateia/keynotes/master/devfestne/inference.png) É similar ao auto-connect, mas o inference calcula e define as contrainst para todas as views e não apenas para o elemento selecionado.

---

# Deleting Constraints

Deletando apenas uma constraint

![inline](https://cdn-images-1.medium.com/max/800/1*3R6V6gjFcEkMrmLKCjWWXA.gif)

---

# Deleting Constraints

Deletando todas as constraints

![inline](https://cdn-images-1.medium.com/max/800/1*IZkhLoX9YJzSHewBjwOxog.gif)

---

# View Sizing

![fill](https://codelabs.developers.google.com/codelabs/constraint-layout/img/7fb5ded1aedd7246.png) **Fixed:** O width/height tem tamanho fixo.

![fill](https://codelabs.developers.google.com/codelabs/constraint-layout/img/44fff184b08bc2e4.png) **Any Size[^1]:** Ocupa todo o espaço disponível para satisfazer a restrição.

![fill](https://codelabs.developers.google.com/codelabs/constraint-layout/img/d066cfdb50a039ba.png) **Wrap Content:** A view ira ocupar o espaço que é preciso para renderizar o contéudo.

[^1]: O Any Size é diferente do *match_parent*, ele não ocupa todo o espaço disponível na view pai.

---

# Vertical Bias

Ajuda a posicionar uma view no eixo vertical, ajustando o valor da *bia* em relação a constranit.


![inline](https://cdn-images-1.medium.com/max/800/1*WqX4E4guxi0mEGZdC83nIA.gif)

```xml
<ImageView
	...
	app:layout_constraintVertical_bias="0.5" />
```

---

# Horizontal Bias

Ajuda a posicionar uma view no eixo horizontal, ajustando o valor da *bia* em relação a constranit.

![inline](https://cdn-images-1.medium.com/max/800/1*I7CHCnvinxkuNISi13Xu5Q.gif)

```xml
<ImageView
	...
	app:layout_constraintHorizontal_bias="0.5" />
```
---

# Aspect Ratio

Veja como é fácil adicionar uma view 16:9 ou 4:3, sem precisar criar uma custom view.

```xml 
 <ImageView
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        ...
        app:layout_constraintDimensionRatio="16:9"/>
```

Este recurso exige que uma das dimessões seja **fixed** ou **warp_content** e outra seja **any size**(0dp)

![left 50%](https://raw.githubusercontent.com/felipearimateia/keynotes/master/devfestne/aspect_ratio.png)

---

# Use Case

![](https://codelabs.developers.google.com/codelabs/constraint-layout/img/c1b7d39d232703cb.png)

---

# References

* [Exploring the new Android ConstraintLayout](https://medium.com/exploring-android/exploring-the-new-android-constraintlayout-eed37fe8d8f1#.j6mtaksa6)

* [ConstraintLayout Part 1](http://wiresareobsolete.com/2016/07/constraintlayout-part-1/)

* [New Layout Editor with Constraint Layout](http://tools.android.com/tech-docs/layout-editor)

* [CodeLab](https://codelabs.developers.google.com/codelabs/constraint-layout/index.html#0)

---

# Obrigado!
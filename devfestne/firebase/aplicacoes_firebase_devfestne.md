autoscale: true

## **Construindo Aplicações Android com Firebase**

### Felipe Arimatéia

![](https://lh3.googleusercontent.com/-whXBCDVxIto/Vz2Rsyz-UjI/AAAAAAAAiJc/UjvR-M2b9tY5SyKFkDY6Q_MbusEINRXkQ/w1024-h1024/Firebase_16-logo.png)

---

## **Felipe Arimatéia (Ari)**

Mobile Developer desde de 2010, apaixonado por código e viciado em séries.

![fill](https://raw.githubusercontent.com/felipearimateia/keynotes/master/images/Twitter-48.png) @twiterdoari

![fill](https://raw.githubusercontent.com/felipearimateia/keynotes/master/images/Google%20Plus-48.png) +FelipeArimateia

![fill](https://raw.githubusercontent.com/felipearimateia/keynotes/master/images/GitHub-48.png) felipearimateia

![left](https://raw.githubusercontent.com/felipearimateia/keynotes/master/images/eu_android.jpg)

---

# Firebase

É uma plataforma mobile para auxiliar no desenvolvimento de aplicativos, sem precisar investir em uma estrutura complexa.

---

![original 100%](https://lh3.googleusercontent.com/pmFdSCiNJf4foF41QJvWGKhkB_sn3Lneql4Vk5kos_nP7n3ieddBGnCKsxQxGjl2tl2A-OEd3_az1Yo8kU0tPnDLe2N2uQ=s888)

---

# **Develop**

![100%](https://lh3.googleusercontent.com/UEPr9HCxfBXJnExgl9t_n_-SWHyrgWmPEuOROoBONknO4kkYC-tRVJzCHn9GeSmaKxqq2aB92L1I-Vlc_NqAiWypqsRR35w=s688)

---

# Criando Projeto

- Criar um projeto no [Firebase Console](https://firebase.google.com/console/)
- Adicionar um Android App
- Faça o download do **google-services.json**
- E copie para o diretório do módulo, normalmente é **app/**

---

# Adicionar SDK

No **build.gradle** do diretório raiz adicionar o plugin do google-services

```gradle
buildscript {
    // ...
    dependencies {
        // ...
        classpath 'com.google.gms:google-services:3.0.0'
    }
}
```

---

## Adicionar SDK

* Adicionar o plugin e dependências no **build.gradle**
* Para iniciar é recomendado adicionar o *firebase-core*
* O core já inclui o serviço de **Analytics**.

```gradle

dependencies {
  // ...
  compile 'com.google.firebase:firebase-core:9.6.1'
}

// ADD THIS AT THE BOTTOM
apply plugin: 'com.google.gms.google-services'

```
---

# Analytics

---

O Analytics é o coração das aplicações de sucesso, através dele é possível conhecer e engajar os usuários.

![inline](https://2.bp.blogspot.com/-cFQKsnAFLhM/Vz61uxwMFdI/AAAAAAAAABE/605YsCMoBqA-rj4XJ9G8BM6XdBTADsEKgCLcB/s640/image00.png)

---

## Enviando eventos

```java
private FirebaseAnalytics mFirebaseAnalytics;

// Obtain the FirebaseAnalytics instance.
mFirebaseAnalytics = FirebaseAnalytics.getInstance(this);

Bundle bundle = new Bundle();
bundle.putString(FirebaseAnalytics.Param.ITEM_ID, id);
bundle.putString(FirebaseAnalytics.Param.ITEM_NAME, name);
bundle.putString(FirebaseAnalytics.Param.CONTENT_TYPE, "image");
mFirebaseAnalytics.logEvent(FirebaseAnalytics.Event.SELECT_CONTENT, bundle);

```

---

# Authentication

---

O **Firebase Authentication** oferece os seguintes serviços de autenticação:

* Autenticação via e-mail e senha.
* Redes Sociais: Google, Facebook, Twitter e Github.
* Autenticação Anônima.

---

## Adicionando Autenticação

**Dependência:**

```gradle
compile 'com.google.firebase:firebase-auth:9.6.1'
```

**FirebaseAuth**

```java

private FirebaseAuth mAuth;
// ...
mAuth = FirebaseAuth.getInstance();

```

---

## Criando uma conta

```java
 mAuth.createUserWithEmailAndPassword(email, password)
                .addOnCompleteListener( task -> {
                    Log.d(TAG, "createUserWithEmail:onComplete:" + task.isSuccessful());

                    if (!task.isSuccessful()) {
                        Toast.makeText(EmailPasswordActivity.this, "Authentication failed.",
                                Toast.LENGTH_SHORT).show();
                    }

                    // ...
                });
```

---

## Logando usuário

```java
 mAuth.signInWithEmailAndPassword(email, password)
                .addOnCompleteListener(task -> {
                    Log.d(TAG, "signInWithEmail:onComplete:" + task.isSuccessful());

                    if (!task.isSuccessful()) {
                        Log.w(TAG, "signInWithEmail", task.getException());
                        Toast.makeText(EmailPasswordActivity.this, "Authentication failed.",
                                Toast.LENGTH_SHORT).show();
                    }

                    // ...
                });
```

---

## AuthStateListener

```java
mAuthListener = new FirebaseAuth.AuthStateListener() {
        @Override
        public void onAuthStateChanged(@NonNull FirebaseAuth firebaseAuth) {
            FirebaseUser user = firebaseAuth.getCurrentUser();
            if (user != null) {
                // User is signed in
                Log.d(TAG, "onAuthStateChanged:signed_in:" + user.getUid());
            } else {
                // User is signed out
                Log.d(TAG, "onAuthStateChanged:signed_out");
            }
            // ...
        }
    };
```

---

## Logout

```java
FirebaseAuth.getInstance().signOut();
```

---

# Realtime Database

---

**Firebase Realtime Database** é um banco de dados NoSQL, que sincroniza todos os clientes conectados em tempo real.

* Tempo real
* Off-line
* Acesso direto via SDK

<br>**Dependência:**

```gradle
compile 'com.google.firebase:firebase-database:9.6.1'
```

---

## Estrutura

```json
{
  "users": {
    "alovelace": {
      "name": "Ada Lovelace",
      "contacts": { "ghopper": true },
    },
    "ghopper": { ... },
    "eclarke": { ... }
  }
}
```

---

## Tipo de dados

* String
* Long
* Double
* Boolean
* Map <String, Object>
* List<Object>

---

## Criando referência

```java
FirebaseDatabase  mDatabase = FirebaseDatabase.getInstance();
DatabaseReference myRef =  mDatabase.getReference("users");
```

---

## Salvando dados

```java
@IgnoreExtraProperties
public class User {

    public String username;
    public String email;

    public User() {
        // Default constructor required for calls to DataSnapshot.getValue(User.class)
    }
}
```

```java
private void writeNewUser(String userId, String name, String email) {
    User user = new User(name, email);
    mDatabase.child("users").child(userId).setValue(user);
}
```

---

## Escutando Dados

```java
ValueEventListener postListener = new ValueEventListener() {
    @Override
    public void onDataChange(DataSnapshot dataSnapshot) {
        // Get Post object and use the values to update the UI
        Post post = dataSnapshot.getValue(Post.class);
        // ...
    }

    @Override
    public void onCancelled(DatabaseError databaseError) {
        // Getting Post failed, log a message
        Log.w(TAG, "loadPost:onCancelled", databaseError.toException());
        // ...
    }
};
mPostReference.addValueEventListener(postListener);
```

---

## Ler dado uma vez

```java
final String userId = getUid();
mDatabase.child("users").child(userId).addListenerForSingleValueEvent(
        new ValueEventListener() {
            @Override
            public void onDataChange(DataSnapshot dataSnapshot) {
                // Get user value
                User user = dataSnapshot.getValue(User.class);

                // ...
            }

            @Override
            public void onCancelled(DatabaseError databaseError) {
                Log.w(TAG, "getUser:onCancelled", databaseError.toException());
            }
        });
```

---

## Off-line

```java
FirebaseDatabase.getInstance().setPersistenceEnabled(true);
```

---

# Storage

---

**Firebase Storage** proporciona o uploads e downloads de arquivos.

* Robusto
* Seguro
* Escalável

<br>**Dependências:**

```gradle
compile 'com.google.firebase:firebase-storage:9.6.1'
compile 'com.google.firebase:firebase-auth:9.6.1'
```

---

## Criando referência[^1]

```java

FirebaseStorage storage = FirebaseStorage.getInstance();

// Create a storage reference from our app
StorageReference storageRef = storage.getReferenceFromUrl("gs://<your-bucket-name>");

// Create a reference to "mountains.jpg"
StorageReference mountainsRef = storageRef.child("mountains.jpg");

// Create a reference to 'images/mountains.jpg'
StorageReference mountainImagesRef = storageRef.child("images/mountains.jpg");

```
[^1]:A URL pode ser obtida na seção Storage do [Firebase console](https://firebase.google.com/console/)

---

## Upload

O Firebase permite fazer o upload de stream, dados que estão na memória e arquivos locais.

```java
Uri file = Uri.fromFile(new File("path/to/images/rivers.jpg"));
StorageReference riversRef = storageRef.child("images/"+file.getLastPathSegment());
uploadTask = riversRef.putFile(file);

// Register observers to listen for when the download is done or if it fails
uploadTask.addOnFailureListener(new OnFailureListener() {
    @Override
    public void onFailure(@NonNull Exception exception) {
        // Handle unsuccessful uploads
    }
}).addOnSuccessListener(new OnSuccessListener<UploadTask.TaskSnapshot>() {
    @Override
    public void onSuccess(UploadTask.TaskSnapshot taskSnapshot) {
        // taskSnapshot.getMetadata() contains file metadata such as size, content-type, and download URL.
        Uri downloadUrl = taskSnapshot.getDownloadUrl();
    }
});
```
---

## Download

O Firebase permite fazer o download para memória ou em um arquivo local. E ele também gera uma URL para compartilhamento.

```java
StorageReference  islandRef = storageRef.child("images/island.jpg");

File localFile = File.createTempFile("images", "jpg");

islandRef.getFile(localFile).addOnSuccessListener(new OnSuccessListener<FileDownloadTask.TaskSnapshot>() {
    @Override
    public void onSuccess(FileDownloadTask.TaskSnapshot taskSnapshot) {
        String url = taskSnapshot.getDownloadUrl();
    }
}).addOnFailureListener(new OnFailureListener() {
    @Override
    public void onFailure(@NonNull Exception exception) {
        // Handle any errors
    }
});
```

---

# Cloud Messaging

---

**Firebase Cloud Messaging** (FCM) permite a troca de mensagens e notificações entre plataformas diferentes.

* Direcionamento versátil de mensagens
* Suporte a mensagens de dados e notificações
* Mensagens ascendentes de aplicativos cliente

<br>**Dependência:**

```gradle
compile 'com.google.firebase:firebase-messaging:9.6.1'
```

---

## Como funciona?

![inline](https://firebase.google.com/docs/cloud-messaging/images/messaging-overview.png)

---

## Configuração

É possível gerenciar a criação e atualização de tokens criando um serviço que extenda de `FirebaseInstanceIdService`.

E para processar as mensagens enviadas pelo FCM, é preciso criar um serviço que extenda de `FirebaseMessagingService`.

---

## Manifest

```xml
<service
    android:name=".MyFirebaseMessagingService">
    <intent-filter>
        <action android:name="com.google.firebase.MESSAGING_EVENT"/>
    </intent-filter>
</service>

    ...

  <service
    android:name=".MyFirebaseInstanceIDService">
    <intent-filter>
        <action android:name="com.google.firebase.INSTANCE_ID_EVENT"/>
    </intent-filter>
</service>
```

---

## Obtendo token

```java
@Override
public void onTokenRefresh() {
    // Get updated InstanceID token.
    String refreshedToken = FirebaseInstanceId.getInstance().getToken();
    Log.d(TAG, "Refreshed token: " + refreshedToken);

    // TODO: Implement this method to send any registration to your app's servers.
    sendRegistrationToServer(refreshedToken);
}
```
---

## Processando mensagem

```java
@Override
    public void onMessageReceived(RemoteMessage remoteMessage) {

        // TODO(developer): Handle FCM messages here.
        // Not getting messages here? See why this may be: https://goo.gl/39bRNJ
        Log.d(TAG, "From: " + remoteMessage.getFrom());

        // Check if message contains a data payload.
        if (remoteMessage.getData().size() > 0) {
            Log.d(TAG, "Message data payload: " + remoteMessage.getData());
        }

        // Check if message contains a notification payload.
        if (remoteMessage.getNotification() != null) {
            Log.d(TAG, "Message Notification Body: " + remoteMessage.getNotification().getBody());
        }

        // Also if you intend on generating your own notifications as a result of a received FCM
        // message, here is where that should be initiated. See sendNotification method below.
    }
```

---

# Crash Reporting

---

O **Firebase Crash Reporting** cria relatórios de erro detalhados, ainda é um serviço beta.

* Monitore erros fatais e não fatais
* Colete os dados necessários para diagnosticar problemas
* Integre ao Analytics

 <br>**Dependência:**

 ```gradle
compile 'com.google.firebase:firebase-crash:9.6.1'
 ```

---

## Reportando erros

```java

//Enviando uma exeção
FirebaseCrash.report(new Exception("My first Android non-fatal error"));

//Enviando logs
FirebaseCrash.log("Activity created");
```

---

# Remote Config

O **Firebase Remote Config**  é um serviço de nuvem que permite alterar o comportamento e a aparência do aplicativo sem exigir que os usuários baixem uma nova atualização.

* Disponibilizar rapidamente alterações para a base de usuários do aplicativo
* Personalizar o aplicativo para segmentos da base de usuários
* Executar testes A/B para aprimorar o aplicativo

<br>**Dependência:**

```gradle
compile 'com.google.firebase:firebase-config:9.6.1'
```

---

## Configuração

```java
FirebaseRemoteConfig firebaseRemoteConfig = FirebaseRemoteConfig.getInstance();
FirebaseRemoteConfigSettings configSettings = new FirebaseRemoteConfigSettings.Builder()
                .setDeveloperModeEnabled(BuildConfig.DEBUG)
                .build();
firebaseRemoteConfig.setConfigSettings(configSettings);
firebaseRemoteConfig.setDefaults(R.xml.remote_config_defaults);
```
---

## Valores Defaults
```xml
<?xml version="1.0" encoding="utf-8"?>
<defaultsMap>
    <entry>
        <key>age_min</key>
        <value>15</value>
    </entry>
    <entry>
        <key>age_max</key>
        <value>30</value>
    </entry>
</defaultsMap>
```
---

## Atualizando valores

```java
remoteConfig.fetch().addOnCompleteListener(this, task -> {
  if (task.isSuccessful()) {
    remoteConfig.activateFetched();
  }
});
```

---

## Recuperando valores

```java
long min = remoteConfig.getLong("age_min");
long max = remoteConfig.getLong("age_max");
```

---

# E agora?

---

# Referências

* Documentação - [https://firebase.google.com/docs/](https://firebase.google.com/docs/)
* Exemplo - [https://github.com/firebase/quickstart-android](https://github.com/firebase/quickstart-android)
* Codelab - [https://codelabs.developers.google.com/codelabs/firebase-android/#0](https://codelabs.developers.google.com/codelabs/firebase-android/#0)

---


# Valeu!

![](http://www.lopes.com.br/blog/wp-content/uploads/2014/11/Pampulha-Alberto-Andrich.jpg)

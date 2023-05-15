---
product: campaign
title: Stack trace sous Linux
description: Stack trace sous Linux
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 91662d6d-2177-4440-b31f-7b031bd953cb
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 100%

---

# Stack trace sous Linux{#stack-trace-in-linux}



La **stack trace** représente une trace contenue dans un fichier de type **core**. Ce fichier est généré en cas d&#39;erreur sur la machine. Il peut permettre de connaître l&#39;origine de l&#39;erreur.

>[!NOTE]
>
>* Un fichier **core** se présente sous le nom **core.`<num>`**.
>* Il faut que **gdb - The GNU Debugger** soit installé sur la machine.
>


Le support technique d&#39;Adobe Campaign peut vous demander cette **stack trace**. Pour l&#39;obtenir, saisissez les commandes suivantes sous Linux :

```
su - neolane
gdb nlserver <coreFile>
//You get lots of output but the stack trace (or Back trace) can be obtained with : 
(gdb) bt
// and forward all the output : 
#0 0x0836c189 in ObjectValue::SetPropertyTarget ()
#1 0x082623b3 in CXtkScriptProperty::VDeclareProperties ()
#2 0x0826a835 in CXtkScriptContext::OnGetProperty ()
#3 0x08370b3d in JavaScriptGetProperty ()
#4 0x557b8aa7 in js_Interpret () from /usr/local/neolane/nl6/lib/libmozjs.so
#5 0x557afb97 in js_Execute () from /usr/local/neolane/nl6/lib/libmozjs.so
#6 0x5578921f in JS_ExecuteScript () from /usr/local/neolane/nl6/lib/libmozjs.so
#7 0x08370468 in JavaScriptSource::Evaluate ()
#8 0x0848fa03 in JSTDeliveryContext::ProcessScript ()
#9 0x0848fcb6 in JSTDeliveryContext::ProcessTemplate ()
#10 0x08460d2b in CDeliveryToolbox::CreateMailMessage ()
#11 0x080d51fe in CMtaQueue::PrepareMessages ()
#12 0x080d2b07 in CMtaQueue::Prepare ()
#13 0x080dca38 in CMtaChild::OnRun ()
#14 0x0814792c in ThreadStartRoutine ()
#15 0x55575b63 in start_thread () from /lib/tls/libpthread.so.0
#16 0x5565918a in clone () from /lib/tls/libc.so.6
```

Le support technique d&#39;Adobe Campaign peut vous demander de lancer cette commande à l&#39;aide d&#39;un exécutable spécifique (que nous vous fournirons).

Dans ce cas, exécutez simplement la commande suivante en remplaçant **nlserver** par le fichier exécutable fourni par Adobe Campaign :

```
gdb nlserver <coreFile>
```

Par exemple :

```
gdb nlserver.1823 <coreFile>
```

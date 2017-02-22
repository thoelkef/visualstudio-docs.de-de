---
title: "&lt;description&gt; Element (ClickOnce Deployment) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#description"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<description> element [ClickOnce deployment manifest]"
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;description&gt; Element (ClickOnce Deployment)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Bezeichnet Anwendungsinformationen, die zum Erstellen eines Shell\-Eintrags und eines Eintrags unter **Software** in der Systemsteuerung verwendet werden.  
  
## Syntax  
  
```  
  
      <description   
   publisher   
   product  
   suiteName  
   supportUrl  
/>  
```  
  
## Elemente und Attribute  
 Das `description`\-Element ist erforderlich und befindet sich im `urn:schemas-microsoft-com:asm.v1`\-Namespace.  Es enthält keine untergeordneten Elemente und verfügt über die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`publisher`|Erforderlich.  Bezeichnet beim Konfigurieren der Bereitstellung für die Installation den Unternehmensnamen, der für die Platzierung der Symbole im Windows\-**Startmenü** und dem Eintrag **Software** in der Systemsteuerung verwendet wird.|  
|`product`|Erforderlich.  Bezeichnet den vollständigen Produktnamen.  Wird als Titel für das Symbol verwendet, das im Windows\-**Startmenü** installiert wird.|  
|`suiteName`|Optional.  Bezeichnet einen Unterordner im Ordner `publisher` des **Windows\-Startmenüs**.|  
|`supportUrl`|Optional.  Gibt eine Support\-URL an, die unter **Software** in der Systemsteuerung angezeigt wird.  Außerdem wird zur Anwendungsunterstützung eine Verknüpfung zu dieser URL im **Startmenü** von Windows erstellt, wenn die Bereitstellung für die Installation konfiguriert wird.|  
  
## Hinweise  
 Das Beschreibungselement ist in allen Bereitstellungskonfigurationen erforderlich.  
  
## Beispiel  
 Im folgenden Codebeispiel wird ein `description`\-Element in einem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellungsmanifest veranschaulicht.  Dieses Codebeispiel ist Teil eines umfangreichen Beispiels, das für das Thema [ClickOnce\-Bereitstellungsmanifest](../deployment/clickonce-deployment-manifest.md) bereitgestellt wird.  
  
```  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## Siehe auch  
 [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)
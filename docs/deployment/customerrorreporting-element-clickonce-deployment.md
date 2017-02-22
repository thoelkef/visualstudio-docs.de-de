---
title: "&lt;customErrorReporting&gt; Element (ClickOnce Deployment) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<customErrorReporting> element [ClickOnce deployment manifest]"
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;customErrorReporting&gt; Element (ClickOnce Deployment)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Legt einen URI zur Fehleranzeige fest.  
  
## Syntax  
  
```  
<customErrorReporting  
   uri  
/>  
```  
  
## Hinweise  
 Dieses Element ist optional.  Wenn das Element nicht vorhanden ist, zeigt [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ein Fehlerdialogfeld an, das den Ausnahmestapel aufführt.  Wenn das `customErrorReporting`\-Element vorhanden ist, zeigt [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] stattdessen den vom `uri`\-Parameter festgelegten URI an.  Der Ziel\-URI enthält die äußere Ausnahmeklasse, die innere Außnahmeklasse und die innere Ausnahmemeldung als Parameter.  
  
 Verwenden Sie dieses Element, um der Anwendung Fehlerberichtsfunktionalität hinzuzufügen.  Da der generierte URI Informationen zum Fehlertyp enthält, kann die Website diese Informationen analysieren und z. B. einen geeigneten Bildschirm zur Problembehandlung anzeigen.  
  
## Beispiel  
 Der folgende Ausschnitt zeigt das `customErrorReporting`\-Element zusammen mit dem ggf. erstellten URI.  
  
```  
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />  
  
Example Generated Error:  
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.  
```  
  
## Siehe auch  
 [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)
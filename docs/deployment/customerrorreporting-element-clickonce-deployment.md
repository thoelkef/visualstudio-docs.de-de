---
title: '&lt;CustomErrorReporting&gt; Element (ClickOnce-Bereitstellung) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords: <customErrorReporting> element [ClickOnce deployment manifest]
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
caps.latest.revision: "6"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 238e4c0c0fe9021424b48963eac7d21bf6f9a049
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="ltcustomerrorreportinggt-element-clickonce-deployment"></a>&lt;CustomErrorReporting&gt; Element (ClickOnce-Bereitstellung)
Gibt einen URI an, der bei einem Fehler angezeigt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
<customErrorReporting  
   uri  
/>  
```  
  
## <a name="remarks"></a>Hinweise  
 Dieses Element ist optional. Ohne diese [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ausnahmestapels ein Fehlerdialogfeld angezeigt. Wenn die `customErrorReporting` Element vorhanden ist, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zeigt den URI angegeben, indem Sie stattdessen die `uri` Parameter. Der Ziel-URI enthält äußere Exception-Klasse, die innere Ausnahme-Klasse und der Meldung der inneren Ausnahme als Parameter.  
  
 Verwenden Sie dieses Element, um Fehlerberichte Funktionen an Ihre Anwendung hinzuzufügen. Da der generierte URI Informationen über den Typ des Fehlers enthält, können Ihre Website Informationen und anzeigen, z. B. eine entsprechende Problembehandlung Bildschirm analysieren.  
  
## <a name="example"></a>Beispiel  
 Der folgende Codeausschnitt zeigt die `customErrorReporting` -Element zusammen mit der generierte URI es möglicherweise zu erzeugen.  
  
```  
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />  
  
Example Generated Error:  
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.  
```  
  
## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Bereitstellungsmanifest](../deployment/clickonce-deployment-manifest.md)
---
title: '&lt;CustomErrorReporting&gt; -Element (ClickOnce-Bereitstellung) | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <customErrorReporting> element [ClickOnce deployment manifest]
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7254f5735be3efa45b7ba3be0541996cb6c2cc69
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54997636"
---
# <a name="ltcustomerrorreportinggt-element-clickonce-deployment"></a>&lt;CustomErrorReporting&gt; -Element (ClickOnce-Bereitstellung)
Gibt einen URI an, der bei einem Fehler angezeigt wird.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<customErrorReporting  
   uri  
/>  
```  
  
## <a name="remarks"></a>Hinweise  
 Dieses Element ist optional. Ohne diese [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zeigt ein Fehlerdialogfeld mit den Ausnahmestapel. Wenn die `customErrorReporting` Element vorhanden ist, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zeigt den URI angegeben werden, indem Sie stattdessen die `uri` Parameter. Der Ziel-URI wird die äußere Exception-Klasse, die innere Ausnahme-Klasse und die Meldung der inneren Ausnahme als Parameter enthalten.  
  
 Verwenden Sie dieses Element, um Windows-Fehlerberichterstattung von Funktionen zu Ihrer Anwendung hinzuzufügen. Da der generierte URI Informationen zu den Typ des Fehlers enthält, können Ihre Website, Informationen und die Anzeige, z. B. eine entsprechende Problembehandlung Bildschirm analysieren.  
  
## <a name="example"></a>Beispiel  
 Der folgende Codeausschnitt zeigt die `customErrorReporting` -Element zusammen mit der generierte URI, der es möglicherweise zu erzeugen.  
  
```xml
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />  
  
Example Generated Error:  
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.  
```  
  
## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Bereitstellungsmanifest](../deployment/clickonce-deployment-manifest.md)
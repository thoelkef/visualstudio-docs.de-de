---
title: '&lt;Description- &gt; Element (ClickOnce-Bereitstellung) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#description
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <description> element [ClickOnce deployment manifest]
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cadf4a0b525e5603247748edd63516dc26d8a0b6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187759"
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;Description- &gt; Element (ClickOnce-Bereitstellung)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identifiziert Anwendungsinformationen, die verwendet werden, um in der Systemsteuerung eine shellpräsenz und **ein Element "** Software" zu erstellen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      <description   
   publisher   
   product  
   suiteName  
   supportUrl  
/>  
```  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Das `description` -Element ist erforderlich und befindet sich im `urn:schemas-microsoft-com:asm.v1` -Namespace. Sie enthält keine untergeordneten Elemente und weist die folgenden Attribute auf.  
  
|attribute|Beschreibung|  
|---------------|-----------------|  
|`publisher`|Erforderlich. Identifiziert den Firmennamen, der für die Symbolplatzierung im **Windows-Startmenü** und **das Element Software in der System** Steuerung verwendet wird, wenn die Bereitstellung für die Installation konfiguriert ist.|  
|`product`|Erforderlich. Identifiziert den vollständigen Produktnamen. Wird als Titel für das Symbol verwendet, das im Windows- **Startmenü** installiert ist.|  
|`suiteName`|Optional. Identifiziert einen Unterordner innerhalb des `publisher` Ordners im Windows- **Startmenü** .|  
|`supportUrl`|Optional. Gibt eine Support-URL an **, die im Element Software** in der Systemsteuerung angezeigt wird. Eine Verknüpfung zu dieser URL wird auch für die Anwendungsunterstützung im Windows- **Startmenü** erstellt, wenn die Bereitstellung für die Installation konfiguriert ist.|  
  
## <a name="remarks"></a>Bemerkungen  
 Das Description-Element ist in allen Bereitstellungs Konfigurationen erforderlich.  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel veranschaulicht ein- `description` Element in einem [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Bereitstellungs Manifest. Dieses Codebeispiel ist Teil eines größeren Beispiels, das für das [ClickOnce-Bereitstellungs Manifest](../deployment/clickonce-deployment-manifest.md) -Thema bereitgestellt wird.  
  
```  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [ClickOnce-Bereitstellungsmanifest](../deployment/clickonce-deployment-manifest.md)

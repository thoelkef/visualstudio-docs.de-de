---
title: '&lt;Zeitpläne&gt; -Element (Bootstrapper) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Schedules> element [bootstrapper]
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: c72ee64bcc174bcd11d800bbc8dd0e1b9848b746
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515768"
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;Zeitpläne&gt; -Element (Bootstrapper)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [ &lt;Zeitpläne&gt; -Element (Bootstrapper)](https://docs.microsoft.com/visualstudio/deployment/schedules-element-bootstrapper).  
  
Die `Schedules` Element enthält `Schedule` Elementen, die bestimmte Zeitpunkten, auf welche Befehle, die definiert, durch Definieren der `Command` Element ausgeführt werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Schedules>  
    <Schedule  
        Name  
    >  
        <BuildList />  
        <BeforePackage />  
        <AfterPackage />  
    </Schedule>  
</Schedules>  
```  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Die `Schedules` Element ist ein untergeordnetes Element des der `Product` Element. Jede `Product` Element möglicherweise mindestens eine `Schedules` Element. Die `Schedules` Element besitzt keine Attribute.  
  
## <a name="schedule"></a>Zeitplan  
 Die `Schedule` Element ist ein untergeordnetes Element des der `Schedules` Element. Ein `Schedules` Element benötigen mindestens einen `Schedule` Element.  
  
 `Schedule` weist das folgende Attribut an.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Name`|Erforderlich. Der Name des Zeitplanelements. Dies entspricht der `ScheduleName` Eigenschaft der `Command` Element. Wenn eine `Command` verweist auf den benannten Zeitplan wird nur von der angegebenen Zeiten ausgeführt werden `Schedule` Element. Zeitpläne können auch zugewiesen werden, mit der `FailIf` und `BypassIf` -Elemente, die diese bedingte Tests zu beschränken, auf dem angegebenen Zeitplan ausgeführt. Weitere Informationen finden Sie unter [ \<Befehle >-Element](../deployment/commands-element-bootstrapper.md).|  
  
 Ein angegebener `Schedule` Element möglicherweise genau eines der folgenden untergeordneten Elemente.  
  
## <a name="buildlist"></a>BuildList  
 Die `BuildList` -Element weist das Installationsprogramm aus, um einen Befehl auszuführen, sobald die bootstrapping-Anwendung gestartet wird.  
  
## <a name="beforepackage"></a>BeforePackage  
 Die `BeforePackage` -Element weist das Installationsprogramm aus, um einen Befehl auszuführen, bevor das angegebene Paket installiert wird.  
  
## <a name="afterpackage"></a>AfterPackage  
 Die `AfterPackage` -Element weist das Installationsprogramm aus, um einen Befehl auszuführen, nachdem das angegebene Paket installiert wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [\<Produkt >-Element](../deployment/product-element-bootstrapper.md)   
 [Referenz zum Produkt- und Paketschema](../deployment/product-and-package-schema-reference.md)




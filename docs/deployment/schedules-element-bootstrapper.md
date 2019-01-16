---
title: '&lt;Zeitpläne&gt; -Element (Bootstrapper) | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Schedules> element [bootstrapper]
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 850c94274f783c306fe31fde4d86c9563c928adf
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53894297"
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;Zeitpläne&gt; -Element (Bootstrapper)
Die `Schedules` Element enthält `Schedule` Elementen, die bestimmte Zeitpunkten, auf welche Befehle, die definiert, durch Definieren der `Command` Element ausgeführt werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```xml
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
 Die `Schedules` Element ist ein untergeordnetes Element des der `Product` Element. Jede `Product` Element möglicherweise mindestens eine `Schedules` Element. Das `Schedules` -Element weist keine Attribute auf.  
  
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
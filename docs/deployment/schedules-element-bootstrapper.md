---
title: '&lt;Zeitpläne- &gt; Element (Boots Trapper) | Microsoft-Dokumentation'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2f6e4ae90dbd36dab4f4df7f72d5ecf57ee04b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62927331"
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;Zeitpläne- &gt; Element (Boots Trapper)
Das- `Schedules` Element enthält- `Schedule` Elemente, mit denen bestimmte Zeiten definiert werden, in denen die vom-Element definierten Befehle `Command` ausgeführt werden sollen.

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
 Das- `Schedules` Element ist ein untergeordnetes `Product` Element des-Elements. Jedes `Product` Element kann höchstens ein Element aufweisen `Schedules` . Das `Schedules` -Element weist keine Attribute auf.

## <a name="schedule"></a>Zeitplan
 Das- `Schedule` Element ist ein untergeordnetes `Schedules` Element des-Elements. Ein- `Schedules` Element muss über mindestens ein- `Schedule` Element verfügen.

 `Schedule` weist das folgende Attribut auf.

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|`Name`|Erforderlich. Der Name des Zeit Plan Elements. Dies entspricht der- `ScheduleName` Eigenschaft des- `Command` Elements. Wenn eine `Command` auf den benannten Zeitplan verweist, wird Sie nur zu dem Zeitpunkt ausgeführt, der durch dieses Element angegeben wird `Schedule` . Zeitpläne können auch den `FailIf` -und-Elementen zugeordnet werden `BypassIf` , die diese bedingten Tests auf die Ausführung nach dem angegebenen Zeitplan beschränken. Weitere Informationen finden Sie unter [\<Commands>Element](../deployment/commands-element-bootstrapper.md).|

 Ein bestimmtes `Schedule` Element kann genau eines der folgenden untergeordneten Elemente aufweisen.

## <a name="buildlist"></a>BuildList
 Das- `BuildList` Element weist den Installer an, einen Befehl unmittelbar nach dem Start der Bootstrapping-Anwendung auszuführen.

## <a name="beforepackage"></a>BeforePackage
 Das- `BeforePackage` Element weist das Installationsprogramm an, einen Befehl auszuführen, bevor das angegebene Paket installiert wird.

## <a name="afterpackage"></a>AfterPackage
 Das- `AfterPackage` Element weist das Installationsprogramm an, einen Befehl auszuführen, nachdem das angegebene Paket installiert wurde.

## <a name="see-also"></a>Weitere Informationen
- [\<Product> gewisses](../deployment/product-element-bootstrapper.md)
- [Produkt-und Paket Schema Referenz](../deployment/product-and-package-schema-reference.md)
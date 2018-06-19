---
title: Neuerungen in Live Unit Testing
ms.date: 10-11-2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing
- Live Unit Testing What's New
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: 8e6e0a812839dac9ad8962e12a610a82cb56a1fc
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31974779"
---
# <a name="whats-new-in-live-unit-testing"></a>Neuerungen in Live Unit Testing

In diesem Artikel werden die Neuerungen in Live Unit Testing für jede Visual Studio Version ab Visual Studio 2017 Version 15.3 aufgelistet. Eine Übersicht zur Verwendung von Live Unit Testing finden Sie unter [Live Unit Testing mit Visual Studio 2017](live-unit-testing.md).

## <a name="whats-new-in-live-unit-testing-for-visual-studio-2017-version-154"></a>Neuerungen in Live Unit Testing für Visual Studio 2017 Version 15.4

Ab Visual Studio 2017 Version 15.4 umfasst Live Unit Testing Verbesserungen und Erweiterungen in verschiedenen Bereichen:

- **Verbesserte Erkennbarkeit** Für Benutzer, die die Live Unit Testing-Funktion noch nicht kennen, zeigt die Visual Studio-IDE eine goldene Leiste an, die immer auf Live Unit Testing verweist, wenn der Benutzer eine Projektmappe öffnet, die zwar Komponententests enthält, in der Live Unit Testing jedoch deaktiviert ist. Die in der goldenen Leiste angezeigten Informationen informieren den Benutzer über Live Unit Testing sowie das Aktivieren dieser Funktion. Außerdem werden in der goldenen Leiste Informationen angezeigt, wenn die Voraussetzungen für Live Unit Testing nicht erfüllt sind. Dazu gehören:

   - Testadapter fehlen
   - Ältere Versionen von Testadaptern sind vorhanden
   - Eine Wiederherstellung von NuGet-Paketen wird benötigt, auf die in der Projektmappe verwiesen wird. 

- **Integration mit Taskcenter-Benachrichtigungen** Die Visual Studio-IDE zeigt im Taskcenter jetzt eine Benachrichtigung für die Verarbeitung im Hintergrund für Live Unit Testing an, damit Benutzer einfach nachvollziehen können, was passiert, wenn Live Unit Testing aktiviert ist. Dadurch wird das Hauptproblem beim Starten von Live Unit Testing in einer großen Projektmappe angegangen. Zuvor konnten Benutzer für ein paar Minuten (bis die Abdeckungssymbole angezeigt werden) nicht sehen, ob Live Unit Testing wirklich aktiviert und funktionstüchtig war. Das hat sich geändert.

- **Unterstützung für das MSTest-Framework Version 1:** Live Unit Testing unterstützt drei beliebte Unit Testing-Frameworks: xUnit, NUnit und MSTest. Zuvor hat Live Unit Testing nur funktioniert, wenn Komponententestprojekte für MSTest die Version 2 von MSTest verwendet haben. Ab Visual Studio 2017 Version 15.4 wird auch MSTest Version 1 unterstützt. 

- **Zuverlässigkeit und Leistung:** Live Unit Testing gewährleistet nun, dass das System darauf aufmerksam wird, wenn Projekte den Ladevorgang nicht komplett abgeschlossen haben, und verhindert das Abstürzen von Live Unit Testing. Durch Verbesserungen der Buildleistung wird außerdem vermieden, dass MSBuild-Projekte erneut ausgewertet werden, wenn das System nicht darüber informiert ist, dass Änderungen an der Projektdatei vorgenommen wurden.  

- **Verschiedene Verbesserungen der Benutzeroberfläche:** Die verwirrende Option **Live Test Set – Include/Exclude** (Live Test Set – Einschließen/Ausschließen), die über die rechte Maustaste aufgerufen wird, wurde in **Live Unit Testing Include/Exclude** (Live Unit Testing: Einschließen/Ausschließen) umbenannt. Die Option **Reset clean** (Bereinigung zurücksetzen) im Menü **Test** > **Live Unit Testing** wurde entfernt. Sie kann nun über **Extras** > **Optionen** > **Live Unit Testing** > **Delete Persisted Data** (Persistente Daten löschen) aufgerufen werden.

## <a name="whats-new-in-live-unit-testing-for-visual-studio-2017-version-153"></a>Neuerungen in Live Unit Testing für Visual Studio 2017 Version 15.3

Ab Visual Studio 2017 Version 15.3 umfassen die Live Unit Testing-Funktionen Verbesserungen und Erweiterungen in zwei wichtigen Bereichen:

- Unterstützung für .NET Core und .NET Standard. Sie können Live Unit Testing für .NET Core- und .NET Standard-Projektmappen verwenden, die entweder in C# oder in Visual Basic geschrieben sind.
 
-  Leistungsverbesserungen. Wie Sie merken werden, ist die Leistung nach dem ersten vollständigen Build und der ersten Testausführung unter Live Unit Testing erheblich schneller. Sie werden auch bei den nachfolgenden Starts von Live Unit Testing in der gleichen Projektmappe deutliche Leistungsverbesserungen wahrnehmen. Es werden nun von Live Unit Testing generierte Daten aufbewahrt und so oft wie möglich für Aktualitätsprüfungen wiederverwendet. 
 
Neben diesen wichtigen Ergänzungen enthält Live Unit Testing außerdem die folgenden Verbesserungen: 

- Testmethoden werden jetzt mithilfe eines Becherglassymbols von regulären Methoden unterschieden. Ein leeres Becherglas bedeutet, dass der jeweilige Test nicht in Live Unit Testing enthalten ist. 

- Wenn Sie im UI-Popupfenster eines Abdeckungssymbols für Live Unit Testing auf eine Testmethode klicken, haben Sie die Möglichkeit, den Test direkt in diesem Ausführungskontext im UI-Fenster zu debuggen, ohne den Code-Editor verlassen zu müssen. Dies ist äußerst praktisch, insbesondere wenn Sie einen fehlgeschlagenen Test prüfen.  

- Mehrere zusätzliche konfigurierbare Optionen wurden „Extras/Optionen/Live Unit Testing/Allgemein“ hinzugefügt. Sie können für den für die Live Unit Testing verwendeten Arbeitsspeicher eine Obergrenze festlegen. Außerdem lässt sich der Dateipfad für persistente Live Unit Testing-Daten für die geöffnete Lösung angeben. 

- Mehrere zusätzliche Menüelemente wurden unter dem Menübalken von „Test/Live Unit Testing“ hinzugefügt. **Bereinigt zurücksetzen** löscht die persistenten Daten und generiert sie neu. **Option** navigiert zu „Extras/Optionen/Live Unit Testing/Allgemein“.
  
- Sie können nun die folgenden Attribute verwenden, um im Quellcode anzugeben, dass Sie bestimmte Testmethoden aus Live Unit Testing ausschließen möchten:
   - Für xUnit: `[Trait("Category", "SkipWhenLiveUnitTesting")]`
   - Für NUnit: `[Category("SkipWhenLiveUnitTesting")]`
   - Für MSTest: `[TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Siehe auch
[Introducing Live Unit Testing (Einführung in Live Unit Testing)](live-unit-testing-intro.md)   
[Live Unit Testing with Visual Studio 2017 (Live Unit Testing mit Visual Studio 2017)](live-unit-testing.md)


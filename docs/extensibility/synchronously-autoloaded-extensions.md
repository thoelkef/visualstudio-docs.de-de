---
title: Synchron automatisch geladene Erweiterungen
ms.date: 02/16/2019
ms.topic: conceptual
ms.assetid: 822e3cf8-f723-4ff1-8467-e0fb42358a1f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad3831fb06d23f622f85a55f5efd0a5650ca5e47
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62799029"
---
# <a name="synchronously-autoloaded-extensions"></a>Synchron automatisch geladene Erweiterungen

Synchron automatisch geladen Erweiterungen haben sich negativ auf die Leistung von Visual Studio und konvertiert werden sollen, um asynchrone Autoload stattdessen zu verwenden. In Visual Studio 2019 Preview 2 beginnen, werden Benutzer benachrichtigt, wenn eine Erweiterung synchron automatisch geladen wird. Die Erweiterung wird geladen werden und wie gewohnt funktionieren.

![kompatibilitätswarnung Erweiterung](media/extension-compatibility-warning.png)

Benutzer können Aktionen ausführen:

- Klicken Sie auf **erfahren Sie mehr** , um diese Informationsseite zu erhalten.

- Klicken Sie auf **-Leistung verwalten** zum Öffnen der [Performance Manager Dialogfeld](#performance-manager-dialog) zeigt, dass Leistungsprobleme mit Erweiterungen und Toolfenster.

- Klicken Sie auf **diese Meldung nicht mehr anzeigen** um diese zu schließen. Bei Auswahl dieser Option wird verhindert, dass auch alle künftige Benachrichtigungen synchron-Erweiterungen automatisch geladen. Benutzer weiterhin Benachrichtigungen zu anderen Visual Studio-Features zu erhalten.

### <a name="performance-manager-dialog"></a>Dialogfeld "Performance-Manager"

![Leistung-Dialogfeld "Manager"](media/performance-manager.png)

Alle Erweiterungen, die alle Pakete synchron in alle benutzersitzungen geladen werden, der **veraltete APIs** Registerkarte.

* Benutzer klicken können, auf die **Weitere Informationen zu diesem Problem** zum Sammeln von Informationen zu den veralteten APIs.
* Benutzer können den Migrationsstatus Erweiterung Hersteller erhalten.

Erweiterungsautoren können finden Sie Anweisungen zum Migrieren zu asynchronen Autoload auf Pakete [Migrieren zu einer von AsyncPackage](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration).

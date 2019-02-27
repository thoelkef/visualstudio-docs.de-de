---
title: Synchron automatisch geladen-Erweiterungen
ms.date: 02/16/2019
ms.topic: conceptual
ms.assetid: 822e3cf8-f723-4ff1-8467-e0fb42358a1f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 960fd54564bc25a8338461c30cd8a893e277b5a5
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2019
ms.locfileid: "56844580"
---
# <a name="synchronously-autoloaded-extensions"></a>Synchron automatisch geladen-Erweiterungen

Synchron automatisch geladen Erweiterungen haben sich negativ auf die Leistung von Visual Studio und konvertiert werden sollen, um asynchrone Autoload stattdessen zu verwenden. In Visual Studio 2019 Preview 2 beginnen, werden Benutzer benachrichtigt, wenn eine Erweiterung synchron automatisch geladen wird. Die Erweiterung wird geladen werden und wie gewohnt funktionieren.

![kompatibilitätswarnung Erweiterung](media/extension-compatibility-warning.png)

1. Benutzer klicken können, auf **erfahren Sie mehr** , um diese Informationsseite zu erhalten.

3. Benutzer klicken können, auf **-Leistung verwalten** zum Öffnen der [Performance Manager-Dialogfeld](#performance-manager-dialog) zeigt, dass Leistungsprobleme mit Erweiterungen und Toolfenster.

3. Benutzer klicken können, auf **diese Meldung nicht mehr anzeigen** um diese zu schließen. Bei Auswahl dieser Option wird auch verhindert, dass diese alle zukünftigen Benachrichtigungen synchron-Erweiterungen automatisch geladen ist. Benutzer weiterhin Benachrichtigungen auf andere Funktionen von Visual Studio erhalten.

### <a name="performance-manager-dialog"></a>Dialogfeld "Performance-Manager"

  ![Leistung-Dialogfeld "Manager"](media/performance-manager.png)

Alle Erweiterungen, die synchron alle Pakete in jeder Sitzung des Benutzers geladen werden angezeigt, der **veraltete APIs** Registerkarte.

* Benutzer klicken können, auf die **Weitere Informationen zu diesem Problem** zum Sammeln von Informationen zu den veralteten APIs.
* Benutzer können den Migrationsstatus Erweiterung Hersteller erhalten.

Erweiterungsautoren können finden Sie Anweisungen zum Migrieren zu asynchronen Autoload auf Pakete [Migrieren zu einer von AsyncPackage](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration).

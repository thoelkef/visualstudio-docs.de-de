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
ms.openlocfilehash: d23a19ad42f665f471274ee75f328056dd55b17d
ms.sourcegitcommit: cd21b38eefdea2cdefb53e68e7a30b868e78dd6b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2019
ms.locfileid: "66037101"
---
# <a name="synchronously-autoloaded-extensions"></a>Synchron automatisch geladene Erweiterungen

Synchron automatisch geladen Erweiterungen haben sich negativ auf die Leistung von Visual Studio und konvertiert werden sollen, um asynchrone Autoload stattdessen zu verwenden. In Visual Studio 2019 Preview 2 beginnen, werden Benutzer benachrichtigt, wenn eine Erweiterung synchron automatisch geladen wird. Die Erweiterung wird geladen werden und wie gewohnt funktionieren.

![kompatibilitätswarnung Erweiterung](media/extension-compatibility-warning.png)

Benutzer können Aktionen ausführen:

- Klicken Sie auf **erfahren Sie mehr** , um diese Informationsseite zu erhalten.

- Klicken Sie auf **-Leistung verwalten** zum Öffnen der [Performance Manager Dialogfeld](#performance-manager-dialog) zeigt, dass Leistungsprobleme mit Erweiterungen und Toolfenster.

- Klicken Sie auf **diese Meldung nicht mehr anzeigen** um diese zu schließen. Bei Auswahl dieser Option wird verhindert, dass auch alle künftige Benachrichtigungen synchron-Erweiterungen automatisch geladen. Benutzer weiterhin Benachrichtigungen zu anderen Visual Studio-Features zu erhalten.

## <a name="performance-manager-dialog"></a>Dialogfeld "Performance-Manager"

![Leistung-Dialogfeld "Manager"](media/performance-manager.png)

Alle Erweiterungen, die alle Pakete synchron in alle benutzersitzungen geladen werden, der **veraltete APIs** Registerkarte.

* Benutzer klicken können, auf die **Weitere Informationen zu diesem Problem** zum Sammeln von Informationen zu den veralteten APIs.
* Benutzer können den Migrationsstatus Erweiterung Hersteller erhalten.

Erweiterungsautoren können finden Sie Anweisungen zum Migrieren zu asynchronen Autoload auf Pakete [Migrieren zu einer von AsyncPackage](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration).

## <a name="specify-synchronous-autoload-settings-using-group-policy"></a>Geben Sie synchrone Autoload-Einstellungen, die mithilfe von Gruppenrichtlinien

Visual Studio 2019 Update 1, wird standardmäßig der Visual Studio-Installation blockiert synchron Autoload gestartet. Wenn Sie eine Gruppenrichtlinie aktivieren, können Sie Visual Studio, um synchrone Autoload auf einzelnen Computern zu ermöglichen, konfigurieren. Legen Sie hierzu eine registrierungsbasierte Richtlinie für den folgenden Schlüssel fest:

**HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SynchronousAutoload**

Eintrag = **zulässig**

Wert = (DWORD)
* **0** synchrone Autoload ist nicht zugelassen werden.
* **1** synchrone Autoload ist zugelassen werden.

Weitere Informationen zu synchronen Autoload-Einstellungen in Visual Studio 2019 Update 1 finden Sie unter den [synchrones Verhalten für Autoload](https://aka.ms/AA52xzw) Seite.

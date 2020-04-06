---
title: Synchron automatisch geladene Erweiterungen
ms.date: 12/11/2019
ms.topic: conceptual
ms.assetid: 822e3cf8-f723-4ff1-8467-e0fb42358a1f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab62d235fd6ed4e47e765fc23868acd5c56efcb2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699369"
---
# <a name="synchronously-autoloaded-extensions"></a>Synchron automatisch geladene Erweiterungen

Synchron elastende Erweiterungen haben negative Auswirkungen auf die Leistung von Visual Studio und sollten stattdessen in asynchrones Autoload konvertiert werden. Standardmäßig blockiert Visual Studio 2019 das automatische Laden von Paketen aus jeder Erweiterung und benachrichtigt den Benutzer.

![Warnung zur Erweiterungskompatibilität](media/extension-compatibility-warning-16-1.png.png)

Ihre Möglichkeiten:

- Klicken Sie auf **Synchrones Autoload zulassen,** damit Erweiterungen automatisch geladen werden können. Um diese Einstellung in Visual Studio-Optionen zu ändern, klicken Sie auf Umgebung, dann auf Erweiterungen, und aktivieren Sie dann das Kontrollkästchen "Synchrones automatisches Laden von Erweiterungen zulassen". 

- Klicken Sie auf **Leistung verwalten,** um das [Dialogfeld "Performance Manager"](#performance-manager-dialog) zu öffnen, in dem Leistungsprobleme mit Erweiterungen und Toolfenstern angezeigt werden.

- Klicken Sie auf Diese **Meldung nicht anzeigen für aktuelle Erweiterungen,** um die Benachrichtigung zu schließen und zukünftige Benachrichtigungen von vorhandenen installierten Erweiterungen zu verhindern. Wenn Sie eine neue Erweiterung hinzufügen, die automatisch geladen wird, wird diese Benachrichtigung erneut angezeigt. Sie erhalten weiterhin Benachrichtigungen über andere Visual Studio-Features.

## <a name="performance-manager-dialog"></a>Dialog mit dem Leistungs-Manager

![Performance Manager-Dialog](media/performance-manager.png)

Alle Erweiterungen, die Pakete in benutzersitzungen synchron geladen haben, werden auf der Registerkarte **Veraltete APIs** angezeigt.

* Klicken Sie auf weitere Informationen zu **diesem Problem,** um weitere Informationen zu den veralteten APIs zu erhalten.
* Wenden Sie sich für den Migrationsfortschritt an die Erweiterungsanbieter.

## <a name="specify-synchronous-autoload-settings-using-group-policy"></a>Synchrone Autoload-Einstellungen mithilfe von Gruppenrichtlinien angeben

Administratoren können eine Gruppenrichtlinie aktivieren, um das synchrone automatische Laden zu ermöglichen. Legen Sie hierzu eine registrierungsbasierte Richtlinie für den folgenden Schlüssel fest:

**HKEY_LOCAL_MACHINE-SOFTWARE-Richtlinien- und -Microsoft-VisualStudio-Synchron-Autoload**

Eintrag = **Zulässig**

Wert = (DWORD)
* **0** ist synchrones Autoload nicht zulässig
* **1** ist synchrones Autoload erlaubt

## <a name="extension-authors"></a>Erweiterungsautoren
Erweiterungsautoren finden unter [Migrate to AsyncPackage](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/AsyncPackageMigration)Anweisungen zum Migrieren von Paketen zu asynchroner Autoload.

## <a name="see-also"></a>Weitere Informationen
Weitere Informationen zu synchronen Autoload-Einstellungen in Visual Studio 2019 finden Sie auf der Seite [Synchrones Autoladeverhalten.](https://devblogs.microsoft.com/visualstudio/updates-to-synchronous-autoload-of-extensions-in-visual-studio-2019/)

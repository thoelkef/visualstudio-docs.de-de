---
title: 'Vorgehensweise: Fügen Sie eine Abhängigkeit zu einem VSIX-Paket | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee6ebeb776e6aa85d5fba200ac357a7375fa2b99
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341058"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Vorgehensweise: Fügen Sie eine Abhängigkeit zu einem VSIX-Paket

Sie können eine VSIX-Paket-Bereitstellung einrichten, die alle Abhängigkeiten installiert, die noch nicht auf dem Zielcomputer vorhanden sind. Dazu gehören die VSIX-Abhängigkeiten an die *"Source.Extension.vsixmanifest"* Datei.

## <a name="to-add-a-dependency"></a>Eine Abhängigkeit hinzufügen

1. Öffnen der *"Source.Extension.vsixmanifest"* Datei die **Entwurf** anzeigen. Wechseln Sie zu der **Abhängigkeiten** Registerkarte, und klicken Sie auf **neu**.

2. Um eine installierte Erweiterung hinzuzufügen: in der **neue Abhängigkeit hinzufügen** wählen Sie im Dialogfeld **-Erweiterung installiert** dann für die **Namen**, wählen Sie eine Erweiterung in der Liste.

3. Eine andere VSIX hinzufügen, die nicht installiert ist: in der **neue Abhängigkeit hinzufügen** wählen Sie im Dialogfeld **Dateisystem** und verwenden Sie dann die **Durchsuchen** klicken, um die VSIX-Datei auszuwählen.

## <a name="require-a-specific-visual-studio-release"></a>Benötigen Sie eine bestimmte Version von Visual Studio

Wenn die Erweiterung eine bestimmte Version von Visual Studio 2017 erforderlich ist, z. B. ein Feature in Version 15.3 hängt, können Sie die Nummer des Builds angeben, in VSIX Einbeziehen **"installationtarget"** . Beispielsweise hat in Version 15.3 eine Buildnummer von "15.0.26730.3". Sehen Sie die Zuordnung von Releases fest, erstellen Sie Zahlen [hier](../install/visual-studio-build-numbers-and-release-dates.md). Beachten Sie, dass mit der Versionsnummer "15.3" nicht ordnungsgemäß funktionieren.

Wenn Ihre Erweiterung erforderlich, Version 15.3 ist oder höher verwenden, müssten Sie deklarieren die **"installationtarget" Version** als [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

Die VSIX-Installationsprogramm erkennt von früheren Versionen von Visual Studio und informieren Sie den Benutzer, dass ein neueres Update erforderlich ist.

## <a name="see-also"></a>Siehe auch

- [Referenz zum VSIX-Erweiterung Schema 1.0](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
- [Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md)
- [Vorbereiten von Erweiterungen für Windows Installer-Bereitstellung](../extensibility/preparing-extensions-for-windows-installer-deployment.md)

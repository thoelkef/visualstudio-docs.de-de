---
title: 'Gewusst wie: Hinzufügen einer Abhängigkeit zu einem VSIX-Paket | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f8b350f063c28762edf90edfe71330534451c75d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711079"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Gewusst wie: Hinzufügen einer Abhängigkeit zu einem VSIX-Paket

Sie können eine VSIX-Paketbereitstellung einrichten, die alle Abhängigkeiten installiert, die noch nicht auf dem Zielcomputer vorhanden sind. Um dies zu erreichen, schließen Sie die VSIX-Abhängigkeiten in die Datei *source.extension.vsixmanifest* ein.

## <a name="to-add-a-dependency"></a>So fügen Sie eine Abhängigkeit hinzu

1. Öffnen Sie die Datei *source.extension.vsixmanifest* in der **Entwurfsansicht.** Wechseln Sie zur Registerkarte **Abhängigkeiten,** und klicken Sie auf **Neu**.

2. Um eine installierte Erweiterung hinzuzufügen: Wählen Sie im Dialogfeld **Neue Abhängigkeit hinzufügen** die Option **Installierte Erweiterung** aus, und wählen Sie dann für den **Namen**eine Erweiterung in der Liste aus.

3. Um eine weitere VSIX hinzuzufügen, die nicht installiert ist: Wählen Sie im Dialogfeld **Neue Abhängigkeit hinzufügen** die Option Datei im **Dateisystem** aus, und verwenden Sie dann die Schaltfläche **Durchsuchen,** um die VSIX auszuwählen.

## <a name="require-a-specific-visual-studio-release"></a>Erfordern einer bestimmten Visual Studio-Version

Wenn Ihre Erweiterung z. B. eine bestimmte Version von Visual Studio 2017 erfordert, hängt dies von einem feature ab, das in 15.3 veröffentlicht wurde, und Sie können die Buildnummer in Ihrem VSIX **InstallationTarget**angeben. Version 15.3 hat beispielsweise die Buildnummer '15.0.26730.3'. Sie können die Zuordnung von Releases zum Erstellen von Nummern [hier](../install/visual-studio-build-numbers-and-release-dates.md)sehen. Beachten Sie, dass die Verwendung der Versionsnummer '15.3' nicht ordnungsgemäß funktioniert.

Wenn Ihre Erweiterung 15.3 oder höher erfordert, würden Sie die **InstallationTarget-Version** als [15.0.26730.3, 16.0) deklarieren:

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

Der VSIXInstaller erkennt frühere Versionen von Visual Studio und informiert den Benutzer, dass ein späteres Update erforderlich ist.

## <a name="see-also"></a>Weitere Informationen

- [VSIX-Erweiterungsschema 1.0-Referenz](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
- [Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md)
- [Vorbereiten von Erweiterungen für die Windows Installer-Bereitstellung](../extensibility/preparing-extensions-for-windows-installer-deployment.md)

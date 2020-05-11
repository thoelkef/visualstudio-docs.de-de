---
title: 'Gewusst wie: Aktualisieren einer Visual Studio-Erweiterung | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 266c0a49db1bca03cec0eb68301445102173df3d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710656"
---
# <a name="how-to-update-a-visual-studio-extension"></a>Gewusst wie: Aktualisieren einer Visual Studio-Erweiterung
Sie können eine Visual Studio-Erweiterung auf Ihrem System aktualisieren, indem Sie **Erweiterungen und Updates** verwenden, um die aktualisierte Version zu installieren. Wenn Sie eine aktualisierte Version einer Erweiterung erstellen, können Sie sie als aktualisiert kennstufend kennstufen, indem Sie die Versionsnummer im VSIX-Manifest erhöhen.

 Updates werden installiert, wenn das VSIX-Manifest `ID` der eingehenden Erweiterung `Version` das gleiche wie das installierte und eine höhere Anzahl hat. Wenn `Version` die Zahl gleich oder niedriger ist, kann das Paket nicht installiert werden. Wenn `ID` die Werte nicht übereinstimmen, wird das noch nicht installierte Paket als separate Erweiterung erkannt.

 Um Konflikte während der Entwicklung zu vermeiden, wird empfohlen, frühere Versionen der laufenden Erweiterungen zu deinstallieren sowie andere potenziell in Konflikt stehende Erweiterungen zu deinstallieren oder zu deaktivieren.

## <a name="to-update-an-extension-on-your-system"></a>So aktualisieren Sie eine Erweiterung auf Ihrem System

1. Klicken Sie im Menü **Extras** auf **Erweiterungen und Updates**.

2. Klicken Sie im linken Bereich auf **Updates**.

3. Klicken Sie im mittleren Bereich auf das Update, das Sie installieren möchten.

     Die Versionsnummer der aktualisierten Erweiterung wird zusammen mit anderen Informationen im rechten Bereich angezeigt.

4. Klicken Sie unten im rechten Bereich auf **Aktualisieren**.

## <a name="to-publish-an-update-of-an-extension"></a>So veröffentlichen Sie eine Aktualisierung einer Erweiterung

1. Öffnen Sie in Visual Studio die Lösung für die Erweiterung, die Sie aktualisieren möchten. Nehmen Sie die Änderungen vor.

    > [!IMPORTANT]
    > Nicht signiert alle Benutzererweiterungen werden nicht automatisch aktualisiert. Sie sollten Ihre Erweiterungen immer signieren.

2. Im **Projektmappen-Explorer**open *source.extension.manifest*.

3. Erhöhen Sie im Manifest-Designer den Wert der Zahl im Feld **Version.**

4. Speichern Sie die Lösung, und erstellen Sie sie.

5. Laden Sie die neue *.vsix-Datei* (im Ordner *-bin-Debug\* des Projekts) auf die Visual Studio [Marketplace-Website](https://marketplace.visualstudio.com/vs) hoch.

     Wenn ein Benutzer, der über eine frühere Version der Erweiterung verfügt, **Erweiterungen und Updates**öffnet, wird die neue Version in der Liste **Updates** angezeigt, vorausgesetzt, das Tool ist so eingestellt, dass es automatisch nach Updates sucht.

     Sie können die automatische Überprüfung auf Updates am unteren Rand des Fensters**Environment** >  **Updates** aktivieren oder deaktivieren ( Automatische**Erkennung verfügbarer Updates aktivieren/deaktivieren**), wodurch die Einstellung **"Auf Updates prüfen"** in**Umgebungserweiterungen und Updates**für**Tools-Optionen** >  **Tools** > geändert wird.

    > [!NOTE]
    > Ab Visual Studio 2015 Update 2 können Sie (in **Tools** > **Options** > **Environment** > **Extensions and Updates**) angeben, ob sie automatische Updates für Benutzererweiterungen, alle Benutzererweiterungen oder beides (Standardeinstellung) wünschen.

## <a name="see-also"></a>Weitere Informationen
- [Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md)
- [Suchen und Verwenden von Visual Studio-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md)

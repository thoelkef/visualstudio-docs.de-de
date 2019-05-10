---
title: Aktualisieren Sie eine Erweiterung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0d1464cdd2be79cd93a3e98bcf8769e8f4b8b89f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435881"
---
# <a name="how-to-update-a-visual-studio-extension"></a>Vorgehensweise: Aktualisieren einer Visual Studio-Erweiterung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können mithilfe von Visual Studio-Erweiterung auf Ihrem System aktualisieren **Erweiterungen und Updates** um die aktualisierte Version zu installieren. Wenn Sie eine aktualisierte Version der Erweiterung erstellen, können Sie es angeben, wie durch das Erhöhen der Versionsnummer im VSIX-Manifest aktualisiert.

 Updates werden installiert, wenn das VSIX-Manifest der eingehenden Erweiterung hat `ID` als der installierten Version und eine höhere `Version` Anzahl. Wenn die `Version` Anzahl ist gleich oder niedriger ist, die das Paket nicht installiert werden kann. Wenn die `ID` Werte stimmen nicht überein, das Paket, das noch nicht installiert ist, wird als separate Erweiterung erkannt.

 Um Konflikte bei der Entwicklung zu vermeiden, empfehlen wir, dass Sie frühere Versionen der Erweiterungen, die ausgeführt wird, deinstallieren und auch deinstallieren oder deaktivieren Sie alle anderen potenziell widersprüchlichen Erweiterungen.

### <a name="to-update-an-extension-on-your-system"></a>Um eine Erweiterung auf Ihrem System zu aktualisieren.

1. Klicken Sie im Menü **Extras** auf **Erweiterungen und Updates**.

2. Klicken Sie im linken Bereich auf **Updates**.

3. Klicken Sie im mittleren Bereich auf das Update aus, die, das Sie installieren möchten.

     Die Versionsnummer der aktualisierte Erweiterung wird im rechten Bereich, zusammen mit anderen Informationen angezeigt.

4. Klicken Sie unten im rechten Bereich auf **Update**.

### <a name="to-publish-an-update-of-an-extension"></a>So veröffentlichen Sie ein Update einer Erweiterung

1. Öffnen Sie in Visual Studio die Projektmappe für die Erweiterung, die Sie aktualisieren möchten. Stellen Sie die Änderungen.

    > [!IMPORTANT]
    > Unsigned alle Benutzererweiterungen nicht automatisch aktualisiert werden. Sie sollten immer Ihre Erweiterungen signieren.

2. In **Projektmappen-Explorer**, öffnen Sie "Source.Extension.vsixmanifest".

3. Erhöhen Sie im manifest-Designer, den Wert der Zahl in die **Version** Feld.

4. Speichern Sie die Projektmappe, und erstellen Sie sie.

5. Die neue VSIX-Datei (in der "\bin\Debug\" des Projekts) zum Hochladen der [Visual Studio Marketplace](https://marketplace.visualstudio.com/) Website.

     Wenn ein Benutzer mit einer früheren Version der Erweiterung öffnet **Erweiterungen und Updates**, die neue Version wird angezeigt, der **Updates** aufzulisten, vorausgesetzt, dass das Tool festgelegt wird, automatisch nach Updates gesucht werden soll.

     Können Sie aktivieren oder deaktivieren Sie die automatische Überprüfung auf Updates am unteren Rand der **Updates** Bereich (**aktiviert bzw. deaktiviert die automatische Erkennung der verfügbaren Updates**), welche Änderungen an der **überprüfen Updates** festlegen in **Extras / Optionen / Umgebung / Erweiterungen und Updates**.

    > [!NOTE]
    > Von Visual Studio 2015 Update 2 an können Sie (in **Extras / Optionen / Umgebung / Erweiterungen und Updates**) angeben, ob automatische Updates für Erweiterungen pro Benutzer, alle Benutzererweiterungen oder beides (Standardeinstellung) vorgenommen werden sollen.

## <a name="see-also"></a>Siehe auch
 [Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md) [suchen und Verwenden von Visual Studio-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md)

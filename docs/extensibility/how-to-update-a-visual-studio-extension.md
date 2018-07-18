---
title: 'Vorgehensweise: Aktualisieren eine Visual Studio-Erweiterung | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c37f26ed8215bb7eac360c978ba902c8e95975ba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134674"
---
# <a name="how-to-update-a-visual-studio-extension"></a>Vorgehensweise: Aktualisieren eine Visual Studio-Erweiterung
Sie können mithilfe eine Visual Studio-Erweiterung auf Ihrem System aktualisieren **Erweiterungen und Updates** die aktualisierte Version zu installieren. Wenn Sie eine aktualisierte Version der Erweiterung erstellen, können Sie es anzugeben, wie aktualisiert, indem Sie die Versionsnummer im VSIX-Manifest erhöht.  
  
 Updates werden installiert, wenn der eingehende Erweiterung VSIX-Manifest verfügt `ID` als der installierten und eine höhere `Version` Anzahl. Wenn die `Version` Anzahl ist gleich oder niedriger ist, das Paket kann nicht installiert werden kann. Wenn die `ID` Werte stimmen nicht überein, das Paket, das noch nicht installiert ist, wird als separate Erweiterung erkannt.  
  
 Zum Vermeiden von Konflikten während der Entwicklung, wird empfohlen, Sie deinstallieren frühere Versionen von Erweiterungen läuft, auch deinstallieren oder deaktivieren alle anderen potenziell in Konflikt stehende Erweiterungen.  
  
### <a name="to-update-an-extension-on-your-system"></a>Um eine Erweiterung auf Ihrem System zu aktualisieren.  
  
1.  Klicken Sie im Menü **Extras** auf **Erweiterungen und Updates**.  
  
2.  Klicken Sie im linken Bereich auf **Updates**.  
  
3.  Klicken Sie im mittleren Bereich auf das Update, die, das Sie installieren möchten.  
  
     Die Versionsnummer der aktualisierten Erweiterung wird im rechten Bereich, zusammen mit anderen Informationen angezeigt.  
  
4.  Klicken Sie unten im rechten Bereich auf **Update**.  
  
### <a name="to-publish-an-update-of-an-extension"></a>So veröffentlichen Sie ein Update einer Erweiterung  
  
1.  Öffnen Sie in Visual Studio die Projektmappe für die Erweiterung, die Sie aktualisieren möchten. Nehmen Sie Änderungen vor.  
  
    > [!IMPORTANT]
    >  Unsignierte Erweiterungen für alle Benutzer nicht automatisch aktualisiert werden. Sie sollten immer Ihre Erweiterungen anmelden.  
  
2.  In **Projektmappen-Explorer**, öffnen Sie "Source.Extension.vsixmanifest".  
  
3.  Im manifest-Designer, erhöhen Sie den Wert der Zahl in die **Version** Feld.  
  
4.  Speichern Sie die Projektmappe, und erstellen Sie sie.  
  
5.  Die neue VSIX-Datei (im Ordner "\bin\Debug\" des Projekts) hochladen, um die [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) Website.  
  
     Wenn ein Benutzer mit einer früheren Version der Erweiterung öffnet **Erweiterungen und Updates**, die neue Version wird angezeigt, der **Updates** aufzulisten, vorausgesetzt, dass das Tool festgelegt ist, automatisch nach Updates gesucht werden soll.  
  
     Sie aktivieren oder deaktivieren Sie die automatische Überprüfung auf Updates am unteren Rand der **Updates** Bereich (**aktiviert bzw. deaktiviert die automatische Erkennung der verfügbaren Updates**), welche Änderungen der **überprüfen Updates** festlegen in **Extras / Optionen / Umgebung / Erweiterungen und Updates**.  
  
    > [!NOTE]
    >  Von Visual Studio 2015 Update 2 an können Sie (in **Extras / Optionen / Umgebung / Erweiterungen und Updates**) angeben, ob automatische Updates für Erweiterungen pro Benutzer, alle Benutzererweiterungen oder beides (Standardeinstellung) vorgenommen werden sollen.  
  
## <a name="see-also"></a>Siehe auch  
 [Aufbau eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md)   
 [Suchen und Verwenden von Visual Studio-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md)

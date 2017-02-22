---
title: "Gewusst wie: Aktualisieren von Visual Studio-Erweiterung | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Update-Paket"
  - "Erweiterung aktualisieren"
  - "neue Paketversion"
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Gewusst wie: Aktualisieren von Visual Studio-Erweiterung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können mithilfe von Visual Studio\-Erweiterung auf Ihrem System aktualisieren **Erweiterungen und Updates** die aktualisierte Version zu installieren. Wenn Sie eine aktualisierte Version der Erweiterung erstellen, können Sie es kennzeichnen, erhöhen Sie die Versionsnummer im VSIX\-Manifest aktualisiert.  
  
 Updates werden installiert, wenn das VSIX\-Manifest der eingehenden Erweiterung verfügt `ID` als die installierte Version und eine höhere `Version` Anzahl. Wenn die `Version` Anzahl entspricht oder niedriger ist, das Paket nicht installiert werden kann. Wenn die `ID` stimmen nicht überein, das Paket, das noch nicht installiert ist, wird als separate Erweiterung erkannt.  
  
 Um Konflikte während der Entwicklung zu vermeiden, wird empfohlen, deinstallieren frühere Versionen von Erweiterungen ausgeführt wird, und auch deinstallieren oder deaktivieren alle anderen potenziell in Konflikt stehende Erweiterungen.  
  
### Eine Erweiterung auf Ihrem System aktualisieren  
  
1.  Klicken Sie im Menü **Extras** auf **Erweiterungen und Updates**.  
  
2.  Klicken Sie im linken Bereich auf **Updates**.  
  
3.  Klicken Sie im mittleren Bereich auf das Update, das Sie installieren möchten.  
  
     Die Versionsnummer der aktualisierten Erweiterung wird im rechten Bereich, zusammen mit weiteren Informationen angezeigt.  
  
4.  Klicken Sie unten im rechten Bereich auf **Update**.  
  
### So veröffentlichen Sie ein Update einer Erweiterung  
  
1.  Öffnen Sie in Visual Studio die Projektmappe für die Erweiterung, die Sie aktualisieren möchten. Stellen Sie die Änderungen.  
  
    > [!IMPORTANT]
    >  Vorzeichenlose Erweiterungen für alle Benutzer nicht automatisch aktualisiert werden. Sie sollten Ihre Erweiterungen immer signieren.  
  
2.  In **Projektmappen\-Explorer**, "Source.Extension.vsixmanifest" zu öffnen.  
  
3.  Erhöhen Sie im manifest\-Designer, den Wert der Zahl in die **Version** Feld.  
  
4.  Speichern Sie die Projektmappe, und erstellen Sie sie.  
  
5.  Die neue VSIX\-Datei \(im Ordner "\\bin\\Debug\\" des Projekts\) zum Hochladen der [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) Website.  
  
     Wenn ein Benutzer mit einer früheren Version der Erweiterung öffnet **Erweiterungen und Updates**, die neue Version wird angezeigt, der **Updates** aufzulisten, vorausgesetzt, dass das Tool festgelegt wird, automatisch nach Updates suchen.  
  
     Können Sie aktivieren oder deaktivieren Sie die automatische Überprüfung auf Updates am unteren Rand der **Updates** Bereich \(**aktiviert bzw. deaktiviert die automatische Erkennung der verfügbaren Updates**\), welche Änderungen der **nach Updates suchen** in die Einstellung **Extras \/ Optionen \/ Umgebung \/ Erweiterungen und Updates**.  
  
    > [!NOTE]
    >  Ab Visual Studio 2015 Update 2 können Sie angeben \(in **Extras \/ Optionen \/ Umgebung \/ Erweiterungen und Updates**\) gibt an, ob Sie automatische Updates für Erweiterungen pro Benutzer, alle Benutzer\-Erweiterungen oder beide \(Standardeinstellung\) möchten.  
  
## Siehe auch  
 [Anatomie eines VSIX\-Pakets](../extensibility/anatomy-of-a-vsix-package.md)   
 [Suchen und Verwenden von Visual Studio\-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md)
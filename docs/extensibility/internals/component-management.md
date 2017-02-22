---
title: "Verwaltung von Komponenten | Microsoft Docs"
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
  - "Komponenten-Installation [Visual Studio SDK]"
  - "Datei-Management-Installation [Visual Studio SDK]"
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Verwaltung von Komponenten
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Geräte Aufgaben in Windows Installer als die Windows Installer\-Komponenten \(gelegentlich aufgerufen WICs oder nur Komponenten\).  Ein GUID kennzeichnet jedes WIC, das die grundlegende Einheit der Installation und Verweiszählung für Setupe ist, die Windows Installer.  
  
 Die verschiedenen Produkte verwenden können, um das VSPackage\-Installationsprogramm zu erstellen, wird in dieser Diskussion die Verwendung von Windows Installer\-Datei \(.msi\) an.  Wenn Sie das Installationsprogramm erstellen, müssen Sie die Datei ordnungsgemäß verwaltet werden, damit die korrekte Verweiszählung immer der Fall.  Dadurch beeinflussen verschiedene Versionen des Produkts oder nicht in einer Mischung von sich selbst zu unterbrechen und Uninstall Installation Scenarios.  
  
 Im Windows Installer tritt Verweiszählung für die Teil der Ebene auf.  Sie müssen die Ressourcendateien, Registrierungseinträge usw. — Komponenten in sorgfältig organisiert werden.  Es gibt weitere Ebenen der Organisation, wie Module, Funktionen und Produkte, die in verschiedenen Szenarien unterstützen können.  Weitere Informationen finden Sie unter [Windows Installer\-Grundlagen](../../extensibility/internals/windows-installer-basics.md).  
  
## Richtlinien für die parallele Installation von Erstellungs\-Setups  
  
-   Erstellen von Dateien und Registrierungsschlüssel, die in Versionen in eigenen Komponenten wieder zugänglich gemacht werden kann.  
  
     Dadurch können Sie sie in der nächsten Version auf einfache Weise zu nutzen.  Zum Beispiel registrierten Typbibliotheken, die global registriert werden, Dateierweiterungen andere Elemente in HKEY\_CLASSES\_ROOT usw.  
  
-   Gruppieren Sie freigegebene Komponenten in separate Modules.  
  
     Dadurch können Sie für paralleles bewegliches Vorwärts ordnungsgemäß zu erstellen.  
  
-   Installieren Sie freigegebene Dateien und Registrierungsschlüssel, indem Sie die gleichen Windows Installer\-Komponenten über Versionen verwenden.  
  
     Wenn Sie eine andere Komponente verwenden, werden die Dateien und Registrierungseinträge deinstalliert, wenn ein VSPackage Version deinstalliert wird, sondern ein anderes VSPackage noch installiert ist.  
  
-   Kombinieren Sie nicht die Versionsinformationen versehen und freigegebenen Elemente in derselben Komponente.  
  
     Dies macht es daher nicht freigegebene Elemente in einem globalen Speicherort und Freigeben von Elementen in lokalisierten Speicherorten installieren.  
  
-   Haben nicht freigegeben Registrierungsschlüssel, die das Freigeben von Dateien zeigen.  
  
     In diesem Fall werden die freigegebenen Schlüssel überschrieben, wenn ein anderes Gibt ein VSPackage installiert ist.  Nachdem Sie auf Entfernen, wird die zweite Version der Datei, in die die Schlüssel verweist, gegangen.  
  
## Siehe auch  
 [Auswählen zwischen freigegebenen und versioniert VSPackages](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [VSPackage\-Setup\-Szenarien](../../extensibility/internals/vspackage-setup-scenarios.md)
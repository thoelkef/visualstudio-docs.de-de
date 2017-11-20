---
title: Verwaltung von Komponenten | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 73a3100252dd5ddfcebd791588a4041c8d588e8d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="component-management"></a>Verwaltung von Komponenten
Einheiten von Aufgaben in der Windows Installer werden als Windows Installer-Komponenten (manchmal auch als WICs oder nur Komponenten bezeichnet) bezeichnet. Eine GUID identifiziert jede WIC, also die grundlegende Einheit von Installations- und verweiszählung für Installationen, die Windows Installer verwenden.  
  
 Obwohl Sie mehrere Produkte verwenden können, um Ihr VSPackage-Installationsprogramm erstellen, geht in den in dieser Diskussion davon aus, um die Verwendung von Windows Installer (MSI)-Dateien. Wenn Sie das Installationsprogramm zu erstellen, müssen Sie die Bereitstellung von Dateien, damit die richtige verweiszählung jederzeit geschieht ordnungsgemäß verwalten. Folglich verschiedene Versionen Ihres Produkts nicht stören oder unterbricht miteinander in eine Mischung aus installieren und Deinstallieren von Szenarien.  
  
 Windows Installer tritt auf, der auf der Komponentenebene verweiszählung. Müssen Sie sorgfältig die Ressourcen organisieren – Dateien und Registrierungseinträge usw. – in Komponenten. Es gibt andere Ebenen der Organisation – wie Module, Funktionen und Produkte –, die in verschiedenen Szenarien unterstützen kann. Weitere Informationen finden Sie unter [Grundlagen von Windows Installer](../../extensibility/internals/windows-installer-basics.md).  
  
## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Setup für die Seite-an-Seite Installation Erstellung von Richtlinien  
  
-   Autor Dateien und Registrierungsschlüsseln, die für die Versionen, die in ihren eigenen Komponenten freigegeben werden.  
  
     Dadurch können Sie sie problemlos in der nächsten Version zu verarbeiten. Die Datei z. B. Typbibliotheken, die global registriert sind Erweiterungen, andere Elemente in HKEY_CLASSES_ROOT usw. registriert.  
  
-   Gemeinsam genutzte Komponenten in separaten Mergemodule zu gruppieren.  
  
     Dadurch wird der Autor für Seite-an-Seite-Hostdaten ordnungsgemäß.  
  
-   Installieren Sie freigegebene Dateien und Registrierungsschlüsseln mithilfe der gleichen Windows Installer-Komponenten über Versionen hinweg.  
  
     Wenn Sie eine andere Komponente verwenden, werden Dateien und Registrierungseinträge deinstalliert, wenn eine mit versionsverwaltung durch das VSPackage wird deinstalliert, aber einem anderen VSPackage noch installiert.  
  
-   Mischen Sie mit Versionsangabe und freigegebene Elemente in der gleichen Komponente nicht.  
  
     Auf diese Weise ist es unmöglich, freigegebene Elemente an einem globalen Speicherort und Versionselementen isolierten Speicherorten zu installieren.  
  
-   Geben Sie keine freigegebenen Registrierungsschlüssel, die auf Dateien Versionsnummern verweisen an.  
  
     Wenn Sie dies tun, werden bei der Installation von einem anderen mit versionsverwaltung durch das VSPackage der gemeinsam genutzten Schlüssel überschrieben. Nachdem Sie die zweite Version entfernen, ist die Datei, die der Schlüssel verweist nicht mehr vorhanden.  
  
## <a name="see-also"></a>Siehe auch  
 [Auswählen zwischen freigegebenen und mit Versionsangabe VSPackages](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [VSPackage-Setupszenarien](../../extensibility/internals/vspackage-setup-scenarios.md)
---
title: Verwaltung von Komponenten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 45a2c4fb0f3fa54a2d2b89c8473961143ec3185c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49280331"
---
# <a name="component-management"></a>Verwaltung von Komponenten
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Einheiten von Aufgaben in der Windows Installer werden als Windows Installer-Komponenten (manchmal als WICs oder nur Komponenten bezeichnet) bezeichnet. Eine GUID identifiziert jedes WIC, wird die grundlegende Einheit der Installation und die verweiszählung für Einrichtungen, die Windows Installer verwenden.  
  
 Obwohl Sie mehrere Produkte verwenden können, um Ihre VSPackage-Installationsprogramm zu erstellen, wird für diese Diskussion von Windows Installer (MSI)-Dateien. Wenn Sie das Installationsprogramm zu erstellen, müssen Sie die Bereitstellung, damit die richtige verweiszählung jederzeit geschieht ordnungsgemäß verwalten. Daher verschiedene Versionen des Produkts nicht beeinträchtigen oder Unterbrechung der jeweils anderen eine Mischung aus installieren und Deinstallieren von Szenarien.  
  
 Windows Installer tritt auf, der auf der Komponentenebene verweiszählung. Sie müssen sorgfältig Organisieren Ihrer Ressourcen – Dateien, Registrierungseinträge und So weiter – in Komponenten. Es gibt andere Ebenen der Organisation, z. B. Module, Funktionen und -Produkte –, mit denen in verschiedenen Szenarien. Weitere Informationen finden Sie unter [Windows Installer-Grundlagen](../../extensibility/internals/windows-installer-basics.md).  
  
## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Richtlinien der Erstellung von Setup für Seite-an-Seite-Installation  
  
-   Author-Dateien und Registrierungsschlüssel, die für die Versionen, die in ihren eigenen Komponenten freigegeben werden.  
  
     Dadurch können Sie ganz einfach auf die nächste Version zu verwenden. Die Datei z. B. Typbibliotheken, die global registriert sind Erweiterungen, andere Elemente in HKEY_CLASSES_ROOT und So weiter registriert.  
  
-   Gruppieren Sie gemeinsam genutzte Komponenten werden in separaten Mergemodule.  
  
     Dadurch können Sie vom Autor ordnungsgemäß Seite-an-Seite für die Zukunft.  
  
-   Installieren Sie die freigegebenen Dateien und Registrierungsschlüsseln mithilfe der gleichen Windows Installer-Komponenten über Versionen hinweg.  
  
     Wenn Sie eine andere Komponente verwenden, werden Dateien und Registrierungseinträge deinstalliert, wenn eine mit versionsverwaltung durch das VSPackage wird deinstalliert, aber einem anderen VSPackage ist weiterhin installiert werden.  
  
-   Mischen Sie versioniert und freigegebene Elemente in der gleichen Komponente nicht.  
  
     Auf diese Weise macht es unmöglich, freigegebene Elemente zu einem globalen Speicherort und Versionselementen, isolierte Standorte zu installieren.  
  
-   Haben Sie keine freigegebenen Registrierungsschlüssel, die auf Dateien Versionsnummern verweisen.  
  
     Wenn Sie dies tun, werden bei der Installation von einem anderen mit versionsverwaltung durch das VSPackage die gemeinsam verwendeten Schlüssel überschrieben. Wenn Sie die zweite Version entfernen, ist die Datei, die auf der der Schlüssel verweist nicht mehr vorhanden.  
  
## <a name="see-also"></a>Siehe auch  
 [Auswählen zwischen freigegebenen und mit versionsverwaltung durch das VSPackages](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [VSPackage-Setupszenarien](../../extensibility/internals/vspackage-setup-scenarios.md)


---
title: Komponenten Verwaltung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 56a110f382d0b182eed0ea1a95cd4dabf2877037
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191852"
---
# <a name="component-management"></a>Verwaltung von Komponenten
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aufgaben Einheiten in der Windows Installer werden als Windows Installer Komponenten (manchmal als "wics" oder "nur Komponenten" bezeichnet) bezeichnet. Eine GUID identifiziert jedes WIC, bei dem es sich um die grundlegende Einheit für die Installation und die Verweis Zählung für Setups handelt, die Windows Installer verwenden.  
  
 Obwohl Sie zum Erstellen des VSPackage-Installers mehrere Produkte verwenden können, wird in dieser Erläuterung die Verwendung von Windows Installer-Dateien (MSI-Dateien) vorausgesetzt. Wenn Sie das Installationsprogramm erstellen, müssen Sie die Datei Bereitstellung ordnungsgemäß verwalten, damit die richtige Verweis Zählung immer erfolgt. Folglich stören verschiedene Versionen Ihres Produkts in einer Mischung aus Installations-und Deinstallations Szenarios nicht gegenseitig.  
  
 In Windows Installer erfolgt die Verweis Zählung auf Komponentenebene. Sie müssen ihre Ressourcen sorgfältig organisieren – Dateien, Registrierungseinträge usw. – in Komponenten. Es gibt andere Ebenen der Organisation – z. b. Module, Features und Produkte –, die in verschiedenen Szenarien hilfreich sein können. Weitere Informationen finden Sie unter [Windows Installer Grundlagen](../../extensibility/internals/windows-installer-basics.md).  
  
## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Richtlinien zum Erstellen von Setup für die parallele Installation  
  
- Verfassen von Dateien und Registrierungs Schlüsseln, die von Versionen gemeinsam genutzt werden, in Ihre eigenen Komponenten.  
  
     Dies ermöglicht es Ihnen, Sie problemlos in der nächsten Version zu nutzen. Beispielsweise können Sie Bibliotheken, die Global registriert sind, Dateierweiterungen, andere in HKEY_CLASSES_ROOT registrierte Elemente usw. eingeben.  
  
- Gruppieren Sie freigegebene Komponenten in separaten Mergemodulen.  
  
     Dies hilft Ihnen, ordnungsgemäß zu erstellen, um sich parallel zu entwickeln.  
  
- Installieren Sie freigegebene Dateien und Registrierungsschlüssel, indem Sie die gleichen Windows Installer Komponenten in verschiedenen Versionen verwenden.  
  
     Wenn Sie eine andere Komponente verwenden, werden Dateien und Registrierungseinträge deinstalliert, wenn ein VSPackage mit Versions Angabe deinstalliert wird, aber noch ein anderes VSPackage installiert ist.  
  
- Mischen Sie versionierte und freigegebene Elemente in derselben Komponente nicht.  
  
     Dadurch ist es nicht mehr möglich, freigegebene Elemente an einem globalen Speicherort zu installieren und Elemente mit Versions Angabe für isolierte Standorte zu installieren.  
  
- Verwenden Sie keine freigegebenen Registrierungsschlüssel, die auf Dateien mit Versions Angabe verweisen.  
  
     Wenn Sie dies tun, werden die freigegebenen Schlüssel überschrieben, wenn ein anderes VSPackage mit Versions Angabe installiert wird. Nachdem Sie die zweite Version entfernt haben, ist die Datei, auf die der Schlüssel verweist, nicht mehr vorhanden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Auswählen zwischen freigegebenen und versionierten VSPackages](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [VSPackage-Setupszenarien](../../extensibility/internals/vspackage-setup-scenarios.md)

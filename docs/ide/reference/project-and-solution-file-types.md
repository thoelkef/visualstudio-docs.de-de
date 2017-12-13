---
title: Projekt- und Projektmappen-Dateitypen | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- File Properties.CopyToOutputDirectory
- File Properties.CustomToolNamespace
- File Properties.FileName
- File Properties.FullPath
- File Properties.BuildAction
- File Properties.CustomTool
- FileProperties
helpviewer_keywords:
- suo files
- file types, Visual Studio
- file extensions
- solutions, solution files
- solution files
- .sln files
- Visual Studio, file types and extensions
- extensions, file types
- sln files
- .suo files
- file extensions, Visual Studio
- file types
ms.assetid: 0ba5007b-465d-4efa-b1e4-f0ee68527649
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 744b35962a196e0372d1bd1fa916f247a9195da6
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2017
---
# <a name="project-and-solution-file-types"></a>Projekt- und Projektmappen-Dateitypen
Von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wird eine Vielzahl von Dateitypen unterstützt. In einer bestimmten Installation wird durch die installierten Komponenten ermittelt, welche Dateitypen unterstützt werden. In diesem Thema werden die Arten von Projektmappen und Projektdateitypen aufgeführt, die in typischen Installationen unterstützt werden. Weitere Informationen zu andere Dateitypen erhalten Sie durch die Suche mithilfe der Dateinamenerweiterungen für jeden Typ.  
  
## <a name="solution-files-sln-and-suo"></a>Projektmappendateien (.sln und .suo)  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verwendet zwei Dateitypen (.sln und .suo) zum Speichern der Einstellungen von Projektmappen. Diese Dateien, die allgemein als Projektmappendateien bezeichnet werden, enthalten alle Informationen, die vom Projektmappen-Explorer für die Anzeige einer grafischen Oberfläche zum Verwalten der Dateien benötigt werden. Mithilfe dieser Dateien können Sie sich ganz auf das Projekt und die Ziele konzentrieren und müssen nicht bei jeder Wiederaufnahme der Entwicklung die Umgebungseinstellungen überprüfen.  
  
|Erweiterung|Name|Beschreibung|  
|---------------|----------|-----------------|  
|.sln|[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]-Projektmappe|Organisiert Projekte, Projektelemente und Projektmappenelemente in einer Projektmappe.|  
|.suo|Benutzeroptionen bei Projektmappen|Damit können Sie die Anpassungen auf Benutzerebene verfolgen, die Sie in Visual Studio vorgenommen haben, z. B. Haltepunkte.|  
  
## <a name="project-files"></a>Projektdateien  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verwendet eine Vielzahl von Dateiformaten zum Speichern von projektbezogenen Informationen. Weitere Informationen finden Sie in den folgenden Hilfethemen:  
  
 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]  
 [Für Visual C++-Projekte erstellte Dateitypen](/cpp/ide/file-types-created-for-visual-cpp-projects)    
 [Erstellen und Verwalten von Visual C++-Projekten](/cpp/ide/creating-and-managing-visual-cpp-projects)    
 [Unicode](/cpp/mfc/unicode-in-mfc)  
  
## <a name="see-also"></a>Siehe auch  
 [Projektmappen und Projekte](../../ide/solutions-and-projects-in-visual-studio.md)
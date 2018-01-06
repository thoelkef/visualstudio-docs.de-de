---
title: "Registrieren Dateierweiterungen für Seite-an-Seite-Bereitstellungen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 457f9e5303c71d73467815b581c091dc239c1b63
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="registering-file-name-extensions-for-side-by-side-deployments"></a>Registrieren Dateierweiterungen für Seite-an-Seite-Bereitstellungen
Für VSPackages, die in einer Seite-an-Seite-Umgebung bereitgestellt werden, müssen Sie die Dateierweiterungen, um die richtige Version der Dateien zuzuordnen registrieren [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Registrierung ermöglicht es Benutzern, öffnen Sie das Projekt und die Projektdateien in die entsprechende Version des Elements, wenn Sie eine versionsspezifische-Dateinamenerweiterung verwenden, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Informationen zu Dateierweiterungen](../extensibility/about-file-name-extensions.md)  
 Erläutert, wie die Dateinamenerweiterungen registriert sind.  
  
 [Angeben von Dateihandlern für Dateierweiterungen](../extensibility/specifying-file-handlers-for-file-name-extensions.md)  
 Enthält Informationen zum Registrieren von Anwendungen, die geöffnet werden können, bearbeiten und usw., eine bestimmte Dateinamenerweiterung.  
  
 [Registrieren von Verben für Dateierweiterungen](../extensibility/registering-verbs-for-file-name-extensions.md)  
 Erläutert die Verben zu registrieren.  
  
 [Verwalten von parallelen Dateizuordnungen](../extensibility/managing-side-by-side-file-associations.md)  
 Erläutert das Behandeln von Seite-an-Seite-Installationen in der eine bestimmte Version [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aufgerufen werden soll, um eine Datei zu öffnen.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Unterstützen mehrerer Versionen von Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)  
 Beschreibt Probleme im Zusammenhang mit mehreren Versionen von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und dem VSPackage während der Entwicklung und Bereitstellung für Endbenutzer.
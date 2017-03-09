---
title: "Automatisierungsmodell | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Automatisierung [Visual Studio SDK], Automatisierungsmodell"
ms.assetid: 48ddc192-96ff-46dc-a1fe-df4eb5c62c84
caps.latest.revision: 16
caps.handback.revision: 16
manager: "douge"
---
# Automatisierungsmodell
Für die Erweiterung von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] stellt das Automatisierungsmodell eine Alternative zu VSPackages dar. Das Automatisierungsmodell, von früheren [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Versionen her als Erweiterbarkeitsmodell bekannt, ist eine Programmierschnittstelle, die den Zugriff auf die zugrundeliegenden Routinen ermöglicht, die die integrierte Entwicklungsumgebung \(IDE\) steuern. Dadurch können Sie diese anpassen und automatisieren.  
  
## VSPackages und Automatisierung  
 Die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] SDK\-Dokumentation konzentriert sich auf VSPackages, die mehr Entwicklungspotenzial haben als das Automatisierungsmodell. Sie können z. B. Code für die Objekte im Automatisierungsmodell schreiben, um eine Sprache \(z. B. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) anzupassen. Mit dem Automatisierungsmodell können Sie der IDE jedoch keine neue Sprache hinzufügen. Wenn Sie der Umgebung eine neue Sprache hinzufügen möchten, müssen Sie ein VSPackage entwickeln.  
  
 Das Automatisierungsmodell und das VSPackage\-Modell bilden zusammen den zweiteiligen Ansatz für die Erweiterbarkeit in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Erweiterbarkeit ist die Kapazität, die Funktionalität der IDE zu verbessern und zu erweitern. Automatisierung bezieht sich auf vom Benutzer erstellten Code und Tools, die Aufgaben in der vorhandenen Umgebung automatisieren und die IDE programmatisch steuern. Mit VSPackages hingegen können Sie der IDE neue Funktionalität hinzufügen. Ein VSPackage ist ein gemeinsam erstellbares Objekt mit einer Klassenfactory, das sich selbst durch Implementieren der Schnittstelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> für die IDE zur Verfügung stellt.  
  
 Für Add\-Ins und Assistenten wird das Automatisierungsmodell verwendet, um die Funktionalität der IDE mithilfe der Automatisierungsschnittstellen zu steuern oder zu erweitern . In der Regel stattet Microsoft [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mit vielen Add\-Ins aus. Mit Add\-Ins können Sie neue Befehle in Symbolleisten und Menüs integrieren, Toolfenster hinzufügen oder bestimmte Aufgaben automatisieren, die Sie regelmäßig in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ausführen.  
  
 Als VSPackage\-Entwickler sollten Sie zum Automatisierungsmodell beitragen. Wenn Sie beispielsweise [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mithilfe des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] SDK eine neue Sprache hinzufügen, sollte Ihre Sprache ein robustes Codemodell bereitstellen, welches das bereits vorhandene erweitert. Weitere Informationen finden Sie unter [Das Automatisierungsmodell beitragen.](../extensibility/internals/contributing-to-the-automation-model.md).  
  
## Siehe auch  
 [VSPackages](../extensibility/internals/vspackages.md)   
 [Das Automatisierungsmodell beitragen.](../extensibility/internals/contributing-to-the-automation-model.md)
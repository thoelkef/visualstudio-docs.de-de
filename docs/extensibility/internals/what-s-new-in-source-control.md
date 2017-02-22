---
title: "Was ist neu im Datenquellen-Steuerelement | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Was ist der neue [Visual Studio SDK], Datenquellen-Steuerelement"
  - "Datenquellen-Steuerelement [Visual Studio SDK], Neuigkeiten"
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
caps.latest.revision: 27
caps.handback.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
---
# Was ist neu im Datenquellen-Steuerelement
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] können Sie eine tief integrierte Implementierung einer Quellcodeverwaltung Projektmappe aus der Quellcodeverwaltung ein VSPackage bereitstellen.  In diesem Abschnitt werden die Funktionen der Quellcodeverwaltung VSPackages und bietet eine Übersicht über die Implementierung Bereitstellungsschritte.  
  
## Die Quellcodeverwaltung VSPackage  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] unterstützt zwei Typen von Office\-Projektmappen Quellcodeverwaltung.  In allen Versionen von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], können Sie ein API\-basiertes Quellcodeverwaltungs\-Plug\-In das Plug\-In trotzdem integrieren.  Sie können auch die Quellcodeverwaltung für ein VSPackage erstellen, die eine Integration, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Pfad enthält. für Quellcodeverwaltung Office\-Lösungen, die eine hohe Ebene der Kultiviertheit Autonomie und erfordern.  
  
 VSPackage kann praktisch alle Arten von Funktionen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]hinzufügen.  Eine Quellcodeverwaltung VSPackage wird eine vollständige [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]für das Feature für Quellcodeverwaltung die Benutzeroberfläche bereit, mit dem der Benutzer Hinter der Kommunikation mit dem Quellcodeverwaltungssystem dargestellt wird.  
  
 Die Implementierung einer Quellcodeverwaltung VSPackage erfordert „Nothing“ Strategie oder legt diese fest.  Der Ersteller einer Quellcodeverwaltung VSPackages zu einer erheblichen Mehraufwand Menge muss, wenn er mehrere Schnittstellen Quellcodeverwaltung und neuer Benutzeroberflächenelemente \(Dialogfelder, Menüs und Symbolleisten\) implementiert die gesamte Funktionalität Quellcodeverwaltung, sowie die Schnittstellen investieren, die von einem Paket, um [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]erfolgreich zu integrieren müssen.  
  
 Die folgenden Schritte geben eine allgemeine Übersicht der Quellcodeverwaltung benötigt werden, um ein Paket zu implementieren.  Ausführlichere Informationen finden Sie unter [Erstellen eines VSPackages Datenquellen\-Steuerelement](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
1.  Erstellen Sie ein VSPackage, das einen privaten vorbringt für die Quellcodeverwaltung.  
  
2.  Implementieren Sie die Schnittstelle in der Quelle Steuerelement\-verknüpften Dienste, die von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vorgebracht werden \(z. B. <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> und die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>\-Schnittstelle\).  
  
3.  Registrieren Sie die Quellcodeverwaltung ein VSPackage.  
  
4.  Implementieren Sie alle Quellcodeverwaltung Benutzeroberfläche, z. B. Menüelemente, Dialogfelder, Symbolleisten und Kontextmenüs.  
  
5.  Alle Quelle Steuerelement\-verknüpften Ereignisse werden zur Quellcodeverwaltung VSackage übergeben, wenn es aktiv ist und von VSPackages behandelt werden muss.  
  
6.  Die Quellcodeverwaltung VSPackage muss auf Ereignisse wie der gelauscht werden, die die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>\-Schnittstelle implementieren und Ereignisse des Titel\-Projekt\-Dokuments \(TPD\) \(wie durch die <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>\-Schnittstelle implementiert\) und notwendige Aktion durchführen.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Übersicht](../../extensibility/internals/source-control-integration-overview.md)   
 [Erstellen eines VSPackages Datenquellen\-Steuerelement](../../extensibility/internals/creating-a-source-control-vspackage.md)
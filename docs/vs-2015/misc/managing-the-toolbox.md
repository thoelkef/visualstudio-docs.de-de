---
title: Verwalten der Toolbox | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Toolbox [Visual Studio SDK], automatic tab selection
- Toolbox [Visual Studio SDK], managing
ms.assetid: 3b052047-f6db-46dd-b3bf-da1c348ee410
caps.latest.revision: 33
manager: douge
ms.openlocfilehash: fa9b30429de00f950e4d9de160fe72ece7f06760
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509259"
---
# <a name="managing-the-toolbox"></a>Managing the Toolbox
Die [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] ermöglicht einem VSPackage, z. B. einem Editor oder Designer Verwalten der Mitgliedschaft in und Darstellung von der **Toolbox**.  
  
 Darüber hinaus kann die **Toolbox** selbst mittels Automatisierung verwaltet werden. Weitere Informationen zum Verwalten einer Toolbox mittels Automatisierung finden Sie unter [wie: steuern die Toolbox](http://msdn.microsoft.com/library/c9d8a18a-d2bc-43d4-a803-601bfc6a6599).  
  
## <a name="automatic-toolbox-tab-selection"></a>Automatische Toolbox-Registerkartenauswahl  
 Eine bestimmte Registerkarte oder Kategorie der **Toolbox** kann automatisch basierend auf dem aktuell aktiven Editor oder Designer aktiviert werden. Wenn z. B. ein Forms-Designer aktiviert ist, soll möglicherweise die Registerkarte **Alle Windows Forms** ausgewählt sein.  
  
 Die Unterstützung ist begrenzt auf Editoren und Designer, die Folgendes erfordern:  
  
1.  Die Implementierung eines Factoryobjekts zum Bereitstellen von Instanzen des Editors oder Designers. Weitere Informationen zum Implementieren von einem Designer- oder Editor-Factoryobjekt finden Sie unter [Editorfactorys](../extensibility/editor-factories.md).  
  
2.  Die Registrierung der Toolbox-Registerkarte, die automatisch aktiviert wird, wenn der Editor bzw. Designer angezeigt wird.  
  
## <a name="controlling-the-toolbox"></a>Steuern der Toolbox  
 Automatisierungsunterstützung der [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] bietet die folgenden Schnittstellen zum Bereitstellen von VSPackages größere Kontrolle über die **Toolbox** verwaltet wird.  
  
|Interface|Beschreibung|  
|---------------|-----------------|  
|<xref:System.Drawing.Design.IToolboxService>|Ermöglicht es Anwendungen zu verwalten, hinzufügen und Entfernen von <xref:System.Drawing.Design.ToolboxItem> Objekte aus der **Toolbox**. Ermöglicht zudem die Konfiguration der Darstellung und von **Toolbox** -Kategorien.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>|Ermöglicht Anwendungen, Active-basierte **Toolbox** -Steuerelemente zu verwalten, hinzuzufügen und zu entfernen sowie Kategorien und Darstellung der **Toolbox** zu konfigurieren.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>|Erweitert die Funktionalität der <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> durch die Bereitstellung umfassender Unterstützung für Persistenz und Lokalisierung.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox4>||  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox5>||  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox6>||  
  
 Es gibt bei der Arbeit mit diesen Schnittstellen einige wichtige Punkte zu bedenken:  
  
-   <xref:System.Drawing.Design.IToolboxService> ist nur für VSPackages verfügbar, die auf dem Managed Package Framework basieren.  
  
-   Steuerelemente können nicht direkt hinzugefügt werden, um die **Toolbox** mit <xref:System.Drawing.Design.IToolboxService>.  
  
-   Ein VSPackage muss entweder <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> verwenden, um Steuerelemente hinzuzufügen, oder das Steuerelement in einen Wrapper-Steuerelement hosten, das von <xref:System.Windows.Forms.AxHost> abgeleitet wird.  
  
     Visual Studio enthält das `Aximp.exe`-Tool für die Automatisierung der Einbindung eines ActiveX-Steuerelements in einem Steuerelement, das von <xref:System.Windows.Forms.AxHost> abgeleitet wird. Weitere Informationen finden Sie unter [Aximp.exe (Windows Forms ActiveX Control Importer)](http://msdn.microsoft.com/library/482c0d83-7144-4497-b626-87d2351b78d0).  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>, und <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> sind COM-basierte Schnittstellen, die über die Interop-Assemblys verfügbar sind.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> wird von <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox> abgeleitet und implementiert alle zugehörigen Methoden.  
  
     Objekte erhalten nur eine Instanz von <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> wird nicht von <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> abgeleitet und implementiert nicht die zugehörigen Methoden.  
  
     Objekte, die Funktionalität in beiden Schnittstellen erfordern, müssen Instanzen beider Schnittstellen von der Umgebung erhalten.  
  
-   Beim Arbeiten mit <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>, werden Informationen über die kanonischen (nicht lokalisierten) Namen von Registerkarten von den Methoden <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.GetIDOfTab%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.SetIDOfTab%2A> verarbeitet.  
  
-   Bei Verwendung von <xref:System.Drawing.Design.IToolboxService> entscheidet der implementierende Benutzer über die Verwaltung von lokalisierten Informationen, z. B. von Kategorienamen.  
  
 Verwenden Sie den Einstellungsmechanismus, um für Benutzer das Speichern von **Toolbox** -Einstellungen zu ermöglichen, auf die von Benutzern über den Befehl **Import- und Exporteinstellungen** im Menü **Extras** der IDE zugegriffen wird. Weitere Informationen zur Verwendung von Einstellungen finden Sie unter [Erweitern von Benutzereinstellungen und Optionen](../extensibility/extending-user-settings-and-options.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern der Toolbox](../misc/extending-the-toolbox.md)
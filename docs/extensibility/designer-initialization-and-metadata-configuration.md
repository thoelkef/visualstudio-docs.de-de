---
title: Designer-Initialisierung und Metadatenkonfiguration | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: c0865b62cc2683a8197b5eb6cbc0599d6c063534
ms.lasthandoff: 02/22/2017

---
# <a name="designer-initialization-and-metadata-configuration"></a>Designer-Initialisierung und Metadatenkonfiguration
Bearbeitung von einem Designer oder Designer-Komponente zugeordneten Metadaten und Filter Attribute bietet einen Mechanismus zum zu definieren, welche Tools von einem bestimmten Designer verwendet werden, andere behandeln <xref:System.Type>Objekte (z. B. Datenstrukturen, Klassen oder grafisch Entitäten), wenn der Designer verfügbar ist und wie der Visual Studio IDE konfiguriert ist, um den Designer zu unterstützen (beispielsweise die **Toolbox** Kategorie oder der Registerkarte verfügbar ist).</xref:System.Type>  
  
 Die [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] bietet verschiedene Mechanismen, um die Steuerung der Initialisierung einer des Designers oder Designer-Komponente und die Bearbeitung der zugehörigen Metadaten durch ein VSPackage zu erleichtern.  
  
## <a name="initializing-metadata-and-configuration-information"></a>Initialisieren von Metadaten und Konfigurationsinformationen  
 Da sie bei Bedarf geladen werden, VSPackages kann nicht geladen wurden durch die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Umgebung vor der Instanziierung eines Designers. Daher VSPackages nicht den Standardmechanismus für die Konfiguration von einem Designer oder Designer-Komponente bei der Erstellung der behandeln verwenden ein <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated>Ereignis.</xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> Ein VSPackage implementiert stattdessen eine Instanz der <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>Schnittstelle und registriert sich selbst zum Bereitstellen von Anpassungen, die als Entwurf Fläche Erweiterungen bezeichnet.</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
### <a name="customizing-initialization"></a>Anpassen der Initialisierung  
 Anpassen von einem Designer, eine Komponente oder ein Designer-Oberfläche umfasst:  
  
1.  Ändern die Designer-Metadaten und effektiv ändern, wie eine bestimmte <xref:System.Type>konvertiert oder zugegriffen wird.</xref:System.Type>  
  
     Dies erfolgt normalerweise über die <xref:System.Drawing.Design.UITypeEditor>oder <xref:System.ComponentModel.TypeConverter>Mechanismen.</xref:System.ComponentModel.TypeConverter> </xref:System.Drawing.Design.UITypeEditor>  
  
     Z. B., wenn <xref:System.Windows.Forms>-Basis Designer initialisiert werden, die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Umgebung ändert die <xref:System.Drawing.Design.UITypeEditor>für <xref:System.Web.UI.WebControls.Image>Objekte, die mit dem Designer verwendet werden, um den Ressourcen-Manager verwenden, um Bitmaps anstelle des Dateisystems zu erhalten.</xref:System.Web.UI.WebControls.Image> </xref:System.Drawing.Design.UITypeEditor> </xref:System.Windows.Forms>  
  
2.  Integration mit der Umgebung, z. B. durch Abonnieren von Ereignissen oder Abrufen der Konfigurationsinformationen des Projekts. Projekt-Konfigurationsinformationen abrufen und Abonnieren von Ereignissen durch Abrufen der <xref:System.ComponentModel.Design.ITypeResolutionService>Schnittstelle.</xref:System.ComponentModel.Design.ITypeResolutionService>  
  
3.  Änderung der benutzerumgebung durch Aktivieren der entsprechenden **Toolbox** Kategorien oder durch Einschränken des Designers Anwendbarkeit durch Anwenden einer Instanz von der <xref:System.ComponentModel.ToolboxItemFilterAttribute>Klasse in den Designer.</xref:System.ComponentModel.ToolboxItemFilterAttribute>  
  
### <a name="designer-initialization-by-a-vspackage"></a>Designer-Initialisierung durch ein VSPackage  
 Ein VSPackage sollte Designer Initialisierung durch verarbeiten:  
  
1.  Erstellen ein Objekt, das die <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>Klasse.</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
    > [!NOTE]
    >  Die <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>Klasse sollte nie auf das gleiche Objekt wie die <xref:Microsoft.VisualStudio.Shell.Package>Klasse</xref:Microsoft.VisualStudio.Shell.Package> implementiert werden</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
2.  Registrieren Sie die Klasse implementiert die <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>Unterstützung für das VSPackage-Designer-Erweiterungen durch Anwenden von Instanzen, <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute> <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute>und <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>der Klasse des VSPackage Implementierung <xref:Microsoft.VisualStudio.Shell.Package>.</xref:Microsoft.VisualStudio.Shell.Package> bereitstellt</xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> </xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute> </xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute> </xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
 Wenn eine Designer oder Designer-Komponente erstellt wird, die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Umgebung:  
  
1.  Greift auf jeden registrierten Entwurf Fläche Erweiterungsanbieter.  
  
2.  Instanziiert und initialisiert eine Instanz jeder Entwurf Fläche Erweiterungsanbieter- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>Objekt</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
3.  Jeder Entwurf Fläche Erweiterungsanbieter aufruft <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A>Methode oder <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A>Methode (falls zutreffend).</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> </xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A>  
  
 Bei der Implementierung der <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>-Objekt als Mitglied eines VSPackage ist es wichtig zu wissen:</xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>  
  
1.  Die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Umgebung bietet keine Kontrolle über welche Metadaten oder andere Einstellungen ein bestimmter `DesignSurfaceExtension` des Anbieters ändert. Es ist möglich, dass zwei oder mehr `DesignSurfaceExtension` Designer dieselben Features auf widersprüchliche Weise ändern, mit der letzten Änderung wird die endgültige Anbieter. Es ist unbestimmt zuletzt die Änderung angewendet wird.  
  
2.  Es ist möglich, eine Implementierung der explizit Einschränken der <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>Objekt für durch Anwenden von Instanzen von bestimmten Designer <xref:System.ComponentModel.ToolboxItemFilterAttribute>zu dieser Implementierung.</xref:System.ComponentModel.ToolboxItemFilterAttribute> </xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> Weitere Informationen zu **Toolbox** Element filtern, finden Sie unter <xref:System.ComponentModel.ToolboxItemFilterAttribute>und <xref:System.ComponentModel.ToolboxItemFilterType>.</xref:System.ComponentModel.ToolboxItemFilterType> </xref:System.ComponentModel.ToolboxItemFilterAttribute>  
  
## <a name="additional-metadata-provisioning"></a>Zusätzliche Metadaten-Bereitstellung  
 Ein VSPackage kann die Konfiguration von einem Designer oder -Designer-Komponente als zur Entwurfszeit ändern.  
  
 Die <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>-Klasse programmgesteuert verwendet werden oder auf eine Bereitstellung von einem Designer VSPackage angewendet werden.</xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>  
  
 Eine Instanz der <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>-Klasse wird verwendet, um die Metadaten erstellt, die auf einer Entwurfsoberfläche Komponenten ändern.</xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> Beispielsweise könnte eine Eigenschaft Standardbrowser verwendeten ersetzen <xref:System.Windows.Forms.CommonDialog>-Objekte mit einem benutzerdefinierten Eigenschaftenbrowser.</xref:System.Windows.Forms.CommonDialog>  
  
 Änderungen von einer Instanz von <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>angewendet werden, um ein VSPackage-Implementierung von <xref:Microsoft.VisualStudio.Shell.Package>kann einen der beiden Bereiche haben:</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>  
  
-   Global – für alle neuen Instanzen einer bestimmten Komponente  
  
-   Lokale – bezieht sich nur auf die Instanz der Komponente erstellt, die auf einer Entwurfsoberfläche, die von der aktuellen VSPackage bereitgestellt.  
  
 Die `IsGlobal` Eigenschaft der <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>Instanz angewendet wird, um ein VSPackage-Implementierung von <xref:Microsoft.VisualStudio.Shell.Package>bestimmt dieser Bereich.</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>  
  
 Anwenden des Attributs auf eine Implementierung der <xref:Microsoft.VisualStudio.Shell.Package>mit der <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A>Eigenschaft der <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>Objekt `true`, wie unten ändert den Browser für die gesamte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Umgebung:</xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> </xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> </xref:Microsoft.VisualStudio.Shell.Package>  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
 Wenn das globale Flag, um festgelegt wurde `false`, dann ist die Änderung der Metadaten für den aktuellen Designer, die von der aktuellen VSPackage unterstützt lokale:  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
> [!NOTE]
>  Momentan ist die Entwurfsoberfläche unterstützt nur das Erstellen von Komponenten, und haben daher nur Komponenten können lokalen Metadaten. Im obigen Beispiel, wir haben versucht, eine Eigenschaft, z. B. Ändern der `Color` Eigenschaft eines Objekts. Wenn `false` für das globale Flag übergebene `CustomBrowser` wird nie angezeigt, weil der Designer nie eine Instanz von erstellt `Color`. Wenn das globale Flag auf `false` eignet sich für Komponenten, z. B. Steuerelemente, Zeitgeber und Dialogfelder.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension></xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>   
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute></xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>   
 <xref:System.ComponentModel.ToolboxItemFilterType></xref:System.ComponentModel.ToolboxItemFilterType>   
 [Erweitern der Entwurfszeit-Unterstützung](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)

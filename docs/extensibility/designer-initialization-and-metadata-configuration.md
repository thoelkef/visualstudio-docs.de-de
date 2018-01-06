---
title: Designer-Initialisierung und Metadatenkonfiguration | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 61624d9926f4d984386f1a8b3fe8a575ce465331
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="designer-initialization-and-metadata-configuration"></a>Designer-Initialisierung und Konfigurieren von Metadaten
Bearbeitung von einem Designer oder Designer-Komponente zugeordneten Metadaten "und" Filtern Attribute bietet einen Mechanismus für Anwendungen definieren, welche Tools von einem bestimmten Designer verwendet werden, andere behandeln <xref:System.Type> Objekte (z. B. Datenstrukturen Klassen oder grafische Entitäten), wenn der Designer verfügbar ist, und wie der Visual Studio-IDE für die vom Designer unterstützt konfiguriert ist (für die Instanz die **Toolbox** -Kategorie oder-Registerkarte zur Verfügung steht).  
  
 Die [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] bietet mehrere Mechanismen, um die Steuerung der Initialisierung einer des Designers oder Designer-Komponente und die Bearbeitung der zugehörigen Metadaten von einem VSPackage zu erleichtern.  
  
## <a name="initializing-metadata-and-configuration-information"></a>Initialisieren von Metadaten und Konfigurationsinformationen  
 Da sie bei Bedarf geladen werden, VSPackages kann nicht geladen durch die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Umgebung vor der Instanziierung eines Designers. Aus diesem Grund VSPackages können keine der Standardmechanismus für die Konfiguration von einem Designer oder Designer-Komponente bei der Erstellung, d. h. Behandeln einer <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> Ereignis. Eine VSPackage implementiert stattdessen eine Instanz der <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> -Schnittstelle und registriert sich selbst zum Bereitstellen von Anpassungen, die als "Entwurf-Oberfläche Extensions" bezeichnet.  
  
### <a name="customizing-initialization"></a>Anpassen von Initialisierung  
 Anpassen von einem Designer, eine Komponente oder ein Designer-Oberfläche umfasst:  
  
1.  Ändern die Designer-Metadaten und effektiv ändern, wie eine bestimmte <xref:System.Type> zugegriffen oder konvertiert wird.  
  
     Dies erfolgt in der Regel über die <xref:System.Drawing.Design.UITypeEditor> oder <xref:System.ComponentModel.TypeConverter> Mechanismen.  
  
     Beispielsweise, wenn <xref:System.Windows.Forms>-Basis-Designer werden initialisiert, die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Umgebung ändert die <xref:System.Drawing.Design.UITypeEditor> für <xref:System.Web.UI.WebControls.Image> Objekten mit dem Designer, mit denen den Ressourcen-Manager verwenden, um Bitmaps anstatt im Dateisystem zu erhalten.  
  
2.  Integrieren von der Umgebung, z. B. durch Abonnieren von Ereignissen oder Projektkonfigurationsinformationen abrufen. Projektkonfigurationsinformationen abrufen und Abonnieren von Ereignissen durch Abrufen der <xref:System.ComponentModel.Design.ITypeResolutionService> Schnittstelle.  
  
3.  Änderung von der Umgebung des Benutzers durch Aktivieren der entsprechenden **Toolbox** Kategorien oder beschränken Sie den Designer Anwendbarkeit durch Anwenden einer Instanz von der <xref:System.ComponentModel.ToolboxItemFilterAttribute> Klasse in den Designer.  
  
### <a name="designer-initialization-by-a-vspackage"></a>Designer-Initialisierung durch ein VSPackage  
 Eine VSPackage sollten Designer Initialisierung durch behandeln:  
  
1.  Erstellen ein Objekt, durch die <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> Klasse.  
  
    > [!NOTE]
    >  Die <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> Klasse sollte nie implementiert werden, auf das gleiche Objekt wie die <xref:Microsoft.VisualStudio.Shell.Package> Klasse.  
  
2.  Registrieren Sie die implementierende Klasse <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> als Unterstützung für das VSPackage-Designer-Erweiterungen durch Anwenden von Instanzen von <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>, <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute> und <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> auf die Klasse, die die VSPackage Implementierung von <xref:Microsoft.VisualStudio.Shell.Package> .  
  
 Wenn ein Designer oder eine Designer-Komponente erstellt wird, die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Umgebung:  
  
1.  Greift auf jede Fläche Erweiterungsanbieter registrierten Entwurf.  
  
2.  Instanziiert und initialisiert eine Instanz der einzelnen Entwurf-Oberfläche Erweiterungsanbieter <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> Objekt  
  
3.  Jeder Entwurf-Oberfläche Erweiterungsanbieter aufruft <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> Methode oder <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> -Methode (nach Bedarf).  
  
 Bei der Implementierung der <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> Objekt als Mitglied eines VSPackage, es ist wichtig zu wissen, dass:  
  
1.  Die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Umgebung bietet keinen Einfluss auf welche Metadaten oder andere Konfigurationseinstellungen ein bestimmter `DesignSurfaceExtension` des Anbieters ändert. Es ist möglich, dass mindestens zwei `DesignSurfaceExtension` Anbieter, die die gleiche Designer-Funktion in Konflikt stehenden Möglichkeiten, mit der letzten Änderung wird definitive ändern. Es ist unbestimmt, welche Änderung zuletzt angewendet wird.  
  
2.  Es ist möglich, eine Implementierung der explizit Einschränken der <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> Objekt für durch Anwenden von Instanzen von bestimmten Designer <xref:System.ComponentModel.ToolboxItemFilterAttribute> an, dass diese Implementierung. Weitere Informationen zu **Toolbox** Element filtern, finden Sie unter der <xref:System.ComponentModel.ToolboxItemFilterAttribute> und <xref:System.ComponentModel.ToolboxItemFilterType>.  
  
## <a name="additional-metadata-provisioning"></a>Zusätzliche Metadaten, die Bereitstellung  
 Eine VSPackage kann es sich um die Konfiguration einer-Designer oder der Designer-Komponente außer zur Entwurfszeit ändern.  
  
 Die <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> -Klasse programmgesteuert verwendet werden kann oder auf einem VSPackage, das Bereitstellen von eines Designers angewendet werden.  
  
 Eine Instanz von der <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> Klasse wird verwendet, um die Metadaten erstellt, die auf einer Entwurfsoberfläche Komponenten zu ändern. Beispielsweise könnte zu ersetzen, einen Standard-Eigenschaftenbrowser von verwendet <xref:System.Windows.Forms.CommonDialog> Objekten mit einem benutzerdefinierten Eigenschaftenbrowser.  
  
 Änderungen, die von einer Instanz von bereitgestellten <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> angewendet wird, eine VSPackage Implementierung von <xref:Microsoft.VisualStudio.Shell.Package> kann einen der beiden Bereiche haben:  
  
-   Global – für alle neuen Instanzen einer bestimmten Komponente  
  
-   Lokale--bezieht sich nur auf die Instanz der Komponente erstellt, die auf einer Entwurfsoberfläche als das aktuelle VSPackage bereitgestellt wird.  
  
 Die `IsGlobal` Eigenschaft von der <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> Instanz angewendet werden, um eine VSPackage Implementierung des <xref:Microsoft.VisualStudio.Shell.Package> bestimmt dieser Bereich.  
  
 Anwenden des Attributs an eine Implementierung der <xref:Microsoft.VisualStudio.Shell.Package> mit der <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> Eigenschaft von der <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> -Objekts festgelegt, um `true`, wie im folgenden ändert den Browser für die gesamte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Umgebung:  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
 Wenn das globale Flag, um festgelegt wurde `false`, und klicken Sie dann die Änderung der Metadaten für den aktuellen Designer unterstützt durch das aktuelle VSPackage lokal vorhanden ist:  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
> [!NOTE]
>  Klicken Sie an der aktuellen Zeit die Entwurfsoberfläche unterstützt nur das Erstellen von Komponenten, und daher können nur Komponenten lokalen Metadaten haben. Im obigen Beispiel wir haben versucht, eine Eigenschaft, z. B. Ändern der `Color` Eigenschaft eines Objekts. Wenn `false` für das globale Flag übergebene `CustomBrowser` würden nie angezeigt werden, da es sich bei der Designer tatsächlich nie eine Instanz erstellt `Color`. Wenn das globale Flag auf `false` eignet sich für Komponenten, z. B. Steuerelemente, Timer und Dialogfelder.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>   
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>   
 <xref:System.ComponentModel.ToolboxItemFilterType>   
 [Erweitern der Entwurfszeitunterstützung](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
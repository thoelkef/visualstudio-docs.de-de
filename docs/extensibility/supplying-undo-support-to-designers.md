---
title: "Angabe Rückgängig-Unterstützung für Designer | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 98243c15f5f69a9aecba589b966d56a68201ab2a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="supplying-undo-support-to-designers"></a>Angeben von Rückgängig-Unterstützung für Designer
Designer, z. B. Editor, festzulegen, müssen in der Regel Rückgängig-Vorgängen zu unterstützen, sodass Benutzer ihre zuletzt vorgenommenen Änderungen umzukehren können ein Codeelement zu ändern.  
  
 Den meisten Designern, die in Visual Studio implementiert haben, Rückgängig-Unterstützung, die automatisch von der Umgebung bereitgestellt wird.  
  
 Designer-Implementierungen, die die Funktion zum Rückgängigmachen unterstützen müssen:  
  
-   Rückgängig-Verwaltung bereitstellt, durch die Implementierung der abstrakten Klasse<xref:System.ComponentModel.Design.UndoEngine>  
  
-   Geben Persistenz und CodeDOM-Unterstützung durch Implementieren der <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> und <xref:System.ComponentModel.Design.IComponentChangeService> Klassen.  
  
 Weitere Informationen zum Schreiben von Designern, die mit [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], finden Sie unter [Erweitern der Entwurfszeitunterstützung](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
 Die [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] stellt eine standardmäßige rückgängig-Infrastruktur durch:  
  
-   Bereitstellung rückgängig Implementierungen über die <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> und <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> Klassen.  
  
-   Angeben von Persistenz und CodeDOM-Unterstützung durch die Standardeinstellung <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> und <xref:System.ComponentModel.Design.IComponentChangeService> Implementierungen.  
  
## <a name="obtaining-undo-support-automatically"></a>Rückgängig-Unterstützung abrufen automatisch  
 Alle erstellt im Designer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automatische und vollständige Rückgängig-Unterstützung wurde if-Designer:  
  
-   Nutzt eine <xref:System.Windows.Forms.Control> Basis die Klasse für die Benutzeroberfläche.  
  
-   Verwendet standardmäßige CodeDOM-basierten codegenerierung und Analysesystem für codegenerierung und Persistenz.  
  
     Weitere Informationen zum Arbeiten mit Visual Studio CodeDOM-Unterstützung finden Sie unter [dynamische Quellcodegenerierung und-Kompilierung](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation)  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>Verwenden Sie explizite Designer Rückgängig-Unterstützung  
 Designer müssen ihre eigenen rückgängig-Verwaltung angeben, wenn sie eine grafische Benutzeroberfläche als Adapter anzeigen, als die vom genannten verwenden <xref:System.Windows.Forms.Control>.  
  
 Ein Beispiel hierfür kann ein Produkt mit einer webbasierten grafische Entwurfsoberfläche erstellen anstelle eines [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] basierte grafische Benutzeroberfläche.  
  
 In solchen Fällen müssen Sie dieser Sicht Adapter mit registrieren [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mit <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>, und geben ein expliziter rückgängig.  
  
 Designer bereitstellen CodeDOM und Persistenz unterstützt, wenn sie nicht verwenden müssen die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Generation Codemodell gemäß der <xref:System.CodeDom> Namespace.  
  
## <a name="undo-support-features-of-the-designer"></a>Rückgängig machen Sie Funktionen zur Unterstützung des Designers  
 Die Umgebung SDK bietet standardmäßigen Implementierungen von Schnittstellen, die zum Bereitstellen der Rückgängig-Unterstützung, die mit dem Entwickler, die nicht mit verwendet werden kann <xref:System.Windows.Forms.Control> basierende Klassen für ihre Benutzer-Schnittstellen oder die standardmäßige CodeDOM und Persistenz-Modell.  
  
 Die <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> Klasse leitet sich von der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] <xref:System.ComponentModel.Design.UndoEngine> mit einer Implementierung der Klasse die <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> Klasse zum Verwalten von Rückgängigvorgänge.  
  
 Visual Studio bietet die folgende Funktion Designer rückgängig gemacht werden:  
  
-   Verknüpfter Rollbackvorgang Funktionalität über mehrere Designer.  
  
-   Untergeordnete Einheiten innerhalb eines Designers können mit ihren übergeordneten Elementen interagieren, durch die Implementierung <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> und <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> auf <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>.  
  
 Das SDK-Umgebung bietet CodeDOM und Persistenz durch Angabe:  
  
-   <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>als eine Implementierung von der<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
 Ein <xref:System.ComponentModel.Design.IComponentChangeService> gebotenen die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]'' Entwurfshost.  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>Geben Sie die Rückgängig-Unterstützung mithilfe Umgebung SDK-Funktionen  
 Um Rückgängig-Unterstützung zu erhalten, müssen ein Objekt, das einen Designer implementieren:  
  
-   Instanziieren und initialisieren Sie eine Instanz von der <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> Klasse mit einer gültigen <xref:System.IServiceProvider> Implementierung.  
  
-   Dies <xref:System.IServiceProvider> Klasse muss die folgenden Dienste bereitstellen:  
  
    -   <xref:System.ComponentModel.Design.IDesignerHost>  
  
    -   <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
         Mithilfe von Designern [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] CodeDOM-Serialisierung verwenden möchten <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> bereitgestellt, mit der [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] als seiner Implementierung von der <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>.  
  
         In diesem Fall die <xref:System.IServiceProvider> Klasse bereitgestellt, um die <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> Konstruktor sollte dieses Objekt zurückgeben, als eine Implementierung der <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> Klasse.  
  
    -   <xref:System.ComponentModel.Design.IComponentChangeService>  
  
         Designer unter Verwendung des standardmäßigen <xref:System.ComponentModel.Design.DesignSurface> gebotenen der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Entwurfshost garantiert eine Standardimplementierung der <xref:System.ComponentModel.Design.IComponentChangeService> Klasse.  
  
 Designer implementieren eine <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> basierend rückgängig-Mechanismus automatisch Änderungen nachverfolgt, wenn:  
  
-   Eigenschaft Änderungen werden über die <xref:System.ComponentModel.TypeDescriptor> Objekt.  
  
-   <xref:System.ComponentModel.Design.IComponentChangeService>Ereignisse werden manuell generiert, wenn eine Änderung am undoable ein Commit ausgeführt wird.  
  
-   Änderung im Designer erstellt wurde, im Rahmen einer <xref:System.ComponentModel.Design.DesignerTransaction>.  
  
-   Der Designer wählt explizit Rückgängigeinheiten, die entweder mithilfe der standardmäßigen Rückgängig-Komponente, die durch eine Implementierung von bereitgestellten erstellen <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> oder die Visual Studio-spezifische Implementierung <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>, die sich daraus ableitet <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> und bietet außerdem eine Implementierung von sowohl <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> und <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [Erweitern der Entwurfszeitunterstützung](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
---
title: Bereitstellen von Rückgängig-Unterstützung für Designer | Microsoft-Dokumentation
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
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5ca68d0046e7dc46087fa6de3835bd6246bc58e1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49267357"
---
# <a name="supplying-undo-support-to-designers"></a>Bereitstellen von Rückgängig-Unterstützung für Designer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Designer, z. B. Editor, festzulegen, in der Regel Rückgängig-Vorgängen unterstützen müssen, damit Benutzer ihren letzten Änderungen umgekehrt werden können, wenn Sie ein Codeelement zu ändern.  
  
 Den meisten Designern in Visual Studio implementiert haben, Rückgängig-Unterstützung, die automatisch von der Umgebung bereitgestellt wird.  
  
 Designer-Implementierungen, die für die Rückgängig-Funktion zu unterstützen:  
  
-   Bereitstellen von Rückgängig-Verwaltung durch die Implementierung der abstrakten Basisklasse <xref:System.ComponentModel.Design.UndoEngine>  
  
-   Geben Persistenz und CodeDOM-Unterstützung durch die Implementierung der <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> und <xref:System.ComponentModel.Design.IComponentChangeService> Klassen.  
  
 Weitere Informationen zum Schreiben von Designern, die mit [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], finden Sie unter [Extending Design-Time Support](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
 Die [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] bietet eine standardmäßige rückgängig-Infrastruktur durch:  
  
-   Bereitstellen von Rückgängig-Verwaltung-Implementierungen über die <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> und <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> Klassen.  
  
-   Angeben von Persistenz und CodeDOM-Unterstützung durch die Standardeinstellung <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> und <xref:System.ComponentModel.Design.IComponentChangeService> Implementierungen.  
  
## <a name="obtaining-undo-support-automatically"></a>Erhalten automatisch Rückgängig-Unterstützung  
 Alle Designer erstellt, die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automatische und vollständige Rückgängig-Unterstützung wurde If, den Designer:  
  
-   Verwendet eine <xref:System.Windows.Forms.Control> basierend-Klasse für die Benutzeroberfläche.  
  
-   Nutzt standard CodeDOM-basierten Code-Generierung und Analysesystem für die codegenerierung und Persistenz.  
  
     Weitere Informationen zum Arbeiten mit Visual Studio CodeDOM-Unterstützung finden Sie unter [dynamische Quelle-Codegenerierung und-Kompilierung](http://msdn.microsoft.com/library/d077a3e8-bd81-4bdf-b6a3-323857ea30fb)  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>Verwenden Sie explizite Designer Rückgängig-Unterstützung  
 Designer müssen eigene rückgängig-Verwaltung angeben, wenn sie eine grafische Benutzeroberfläche, bezeichnet als Adapter anzeigen, als die vom verwenden <xref:System.Windows.Forms.Control>.  
  
 Ein Beispiel dafür erstellen möglicherweise ein Produkt mit einer grafischen Designtools von webbasierten Schnittstelle anstelle eines [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] basierte grafische Benutzeroberfläche.  
  
 In solchen Fällen würden müssen diesen ansichtsadapters mit registrieren [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] mit <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>, und geben Sie explizite rückgängig-Verwaltung.  
  
 Designer bereitstellen, CodeDOM und Persistenz unterstützen, wenn sie nicht verwenden, müssen die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Code Generation Muster in den <xref:System.CodeDom> Namespace.  
  
## <a name="undo-support-features-of-the-designer"></a>Rückgängig für Unterstützungsfunktionen des Designers  
 Das SDK-Umgebung stellt standardimplementierungen der Schnittstellen, die zu Rückgängig-Unterstützung, die von Designern, die nicht mit verwendet werden kann <xref:System.Windows.Forms.Control> basierende Klassen für ihren Benutzeroberflächen oder dem Standardmodell CodeDOM und Persistenz.  
  
 Die <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> Klasse leitet sich von der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] <xref:System.ComponentModel.Design.UndoEngine> Klasse mit einer Implementierung des der <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> Klasse zum Verwalten von Rückgängig-Vorgänge.  
  
 Visual Studio bietet die folgenden Funktionen ab, der Designer Rückgängig:  
  
-   Verknüpften Rückgängig-Funktion über mehrere Designer.  
  
-   Untergeordnete Einheiten in einem Designer können mit ihren übergeordneten Elementen interagieren, durch die Implementierung <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> und <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> auf <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>.  
  
 Das SDK-Umgebung bietet CodeDOM und Persistenz durch Angabe:  
  
-   <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> als ein Implementierungen von der <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
 Ein <xref:System.ComponentModel.Design.IComponentChangeService> gebotenen die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]'' Entwurfshost.  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>Umgebung SDK-Funktionen mithilfe von Rückgängig-Unterstützung bereitstellen.  
 Um Rückgängig-Unterstützung zu erhalten, müssen ein Objekt, das einen Designer implementieren:  
  
-   Instanziieren und initialisieren eine Instanz von der <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> Klasse mit einer gültigen <xref:System.IServiceProvider> Implementierung.  
  
-   Dies <xref:System.IServiceProvider> Klasse muss die folgenden Dienste bereitstellen:  
  
    -   <xref:System.ComponentModel.Design.IDesignerHost>.  
  
    -   <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
         Mithilfe von Designern [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] CodeDOM-Serialisierung verwenden möchten <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> im Lieferumfang der [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] als eine Implementierung von der <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>.  
  
         In diesem Fall die <xref:System.IServiceProvider> Klasse bereitgestellt, um die <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> Konstruktor muss dieses Objekt zurückgeben, wie eine Implementierung von der <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> Klasse.  
  
    -   <xref:System.ComponentModel.Design.IComponentChangeService>  
  
         Designer, die über das standardmäßige <xref:System.ComponentModel.Design.DesignSurface> gebotenen die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Entwurfshost sind garantiert eine Standardimplementierung von der <xref:System.ComponentModel.Design.IComponentChangeService> Klasse.  
  
 Implementieren von Designern eine <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> basierend rückgängig-Mechanismus wird automatisch Änderungen nachverfolgt, wenn:  
  
-   Eigenschaftenänderungen erfolgen über die <xref:System.ComponentModel.TypeDescriptor> Objekt.  
  
-   <xref:System.ComponentModel.Design.IComponentChangeService> Ereignisse werden manuell generiert, wenn eine Änderung rückgängig zu machen, ein Commit ausgeführt wird.  
  
-   Änderung im Designer erstellt wurde, im Kontext einer <xref:System.ComponentModel.Design.DesignerTransaction>.  
  
-   Der Designer wählt explizit Rückgängig-Komponenten, die entweder die standardmäßige Rückgängig-Komponente, die durch eine Implementierung der bereitgestellten erstellen <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> oder die Visual Studio-spezifische Implementierung <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>, die sich daraus ableitet <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> und bietet außerdem eine Implementierung von sowohl <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> und <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [Erweitern der Entwurfszeitunterstützung](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)


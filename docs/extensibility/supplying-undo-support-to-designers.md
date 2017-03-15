---
title: "Bereitstellung rückgängig-Unterstützung für Designer | Microsoft-Dokumentation"
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
caps.latest.revision: 17
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
ms.openlocfilehash: 95e6873d0a3b254fa8f34144253a44c0a8cab60d
ms.lasthandoff: 02/22/2017

---
# <a name="supplying-undo-support-to-designers"></a>Bereitstellen von Rückgängig-Unterstützung für Designer
In der Regel müssen wie Editoren, Designer Rückgängig-Vorgängen zu unterstützen, sodass Benutzer ihre aktuellen Änderungen stornieren können, wenn ein Codeelement zu ändern.  
  
 Die meisten Designer in Visual Studio implementiert haben, Rückgängig-Unterstützung, die automatisch von der Umgebung bereitgestellt wird.  
  
 Designer-Implementierungen, die Unterstützung für die Funktion zum Rückgängigmachen bereitzustellen:  
  
-   Bereitstellen Sie rückgängig-Management durch die Implementierung der abstrakten Basisklasse<xref:System.ComponentModel.Design.UndoEngine></xref:System.ComponentModel.Design.UndoEngine>  
  
-   Geben Persistenz und CodeDOM-Unterstützung durch die Implementierung der <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>und der <xref:System.ComponentModel.Design.IComponentChangeService>Klassen.</xref:System.ComponentModel.Design.IComponentChangeService> </xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
 Weitere Informationen zum Schreiben von Designern, die mit [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], finden Sie unter [Extending Design-Time Support](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
 Die [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] bietet eine standardmäßige rückgängig-Infrastruktur durch:  
  
-   Bereitstellung rückgängig machen Implementierung über die <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>und <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>Klassen.</xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> </xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>  
  
-   Bereitstellen von Persistenz und CodeDOM-Unterstützung mit der standardmäßigen <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>und <xref:System.ComponentModel.Design.IComponentChangeService>Implementierungen.</xref:System.ComponentModel.Design.IComponentChangeService> </xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>  
  
## <a name="obtaining-undo-support-automatically"></a>Erhalten automatisch Rückgängig-Unterstützung  
 Jeder Designer erstellt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automatische und vollständige Rückgängig-Unterstützung wurde Fall, wenn der Designer:  
  
-   Verwendet eine <xref:System.Windows.Forms.Control>Klasse für die Benutzeroberfläche basierend.</xref:System.Windows.Forms.Control>  
  
-   Verwendet zum Generieren von CodeDOM-basierten Standardcode und Analysesystem für die Generierung von Code und Persistenz.  
  
     Weitere Informationen zum Arbeiten mit Visual Studio CodeDOM-Unterstützung finden Sie unter [dynamische Quelle generieren und kompilieren](http://msdn.microsoft.com/Library/d077a3e8-bd81-4bdf-b6a3-323857ea30fb)  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>Verwenden Sie explizite Designer Rückgängig-Unterstützung  
 Designer müssen eigene rückgängig-Verwaltung angeben, wenn diese graphical User Interface, bezeichnet als Adapter anzeigen, als eine der bereitgestellten <xref:System.Windows.Forms.Control>.</xref:System.Windows.Forms.Control> verwenden  
  
 Ein Beispiel dafür, erstellen ein Produkts mit einer webbasierten Grafikdesign-Schnittstelle anstelle eines [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] basierte Benutzeroberfläche.  
  
 In solchen Fällen müssen Sie diese Ansicht-Adapter mit registrieren [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mit <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>, und geben ein expliziter rückgängig.</xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>  
  
 Designer bereitstellen, CodeDOM und Persistenz unterstützt, wenn sie nicht verwenden, müssen die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Code Generation Muster in den <xref:System.CodeDom>Namespace.</xref:System.CodeDom>  
  
## <a name="undo-support-features-of-the-designer"></a>Rückgängig-Funktionen zur Unterstützung von des Designers  
 Das SDK-Umgebung bietet standardimplementierungen von Schnittstellen bereitstellen Rückgängig-Unterstützung, die vom Designer nicht mit verwendet werden kann <xref:System.Windows.Forms.Control>basierende Klassen für ihren Benutzeroberflächen oder dem Standardmodell CodeDOM und Persistenz.</xref:System.Windows.Forms.Control>  
  
 Die <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>Klasse leitet sich von der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] <xref:System.ComponentModel.Design.UndoEngine>mithilfe einer Implementierung der Klasse die <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>Klasse zum Verwalten von Rückgängigvorgänge.</xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> </xref:System.ComponentModel.Design.UndoEngine> </xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>  
  
 Visual Studio bietet die folgende Funktionen Designer rückgängig gemacht werden:  
  
-   Verknüpfte Rückgängig-Funktion über mehrere Designer.  
  
-   Untergeordnete Einheiten innerhalb eines Designers können mit ihren übergeordneten Elementen durch die Implementierung <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>und <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>.</xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> </xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> </xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> interagieren.  
  
 Das SDK-Umgebung bietet Unterstützung von CodeDOM und Persistenz durch bereitstellen:  
  
-   <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>als eine Implementierung von der<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService></xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService></xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>  
  
 Ein <xref:System.ComponentModel.Design.IComponentChangeService>gemäß der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]'' Entwurfshost.</xref:System.ComponentModel.Design.IComponentChangeService>  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>Mithilfe der Umgebung SDK-Features Rückgängig-Unterstützung bereitstellen.  
 Um Rückgängig-Unterstützung zu erhalten, müssen ein Objekt, das von einem Designer:  
  
-   Instanziieren und initialisieren Sie eine Instanz der <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>Klasse mit einer gültigen <xref:System.IServiceProvider>Implementierung.</xref:System.IServiceProvider> </xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>  
  
-   Diese <xref:System.IServiceProvider>Klasse muss die folgenden Dienste bereitstellen:</xref:System.IServiceProvider>  
  
    -   <xref:System.ComponentModel.Design.IDesignerHost>.</xref:System.ComponentModel.Design.IDesignerHost>  
  
    -   <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService></xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
         Mithilfe von Designern [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] CodeDOM-Serialisierung verwenden möchten <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>bereitgestellt, mit der [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] zur Implementierung des <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>.</xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> </xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>  
  
         In diesem Fall die <xref:System.IServiceProvider>Klasse bereitgestellt, die der <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>Konstruktor sollte dieses Objekt als eine Implementierung der <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>Klasse</xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> zurückgeben</xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> </xref:System.IServiceProvider>  
  
    -   <xref:System.ComponentModel.Design.IComponentChangeService></xref:System.ComponentModel.Design.IComponentChangeService>  
  
         Mit dem Designer <xref:System.ComponentModel.Design.DesignSurface>gemäß der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Entwurfshost garantiert eine Standard-Implementierung der <xref:System.ComponentModel.Design.IComponentChangeService>Klasse</xref:System.ComponentModel.Design.IComponentChangeService> </xref:System.ComponentModel.Design.DesignSurface>  
  
 Implementieren von Designern eine <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>Basis rückgängig-Mechanismus automatisch Änderungen nachverfolgt, wenn:</xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>  
  
-   Eigenschaft geändert werden über die <xref:System.ComponentModel.TypeDescriptor>Objekt.</xref:System.ComponentModel.TypeDescriptor>  
  
-   <xref:System.ComponentModel.Design.IComponentChangeService>Ereignisse werden manuell generiert, wenn eine Änderung rückgängig zu machen, ein Commit ausgeführt wird.</xref:System.ComponentModel.Design.IComponentChangeService>  
  
-   Änderung im Designer wurde im Kontext eines <xref:System.ComponentModel.Design.DesignerTransaction>.</xref:System.ComponentModel.Design.DesignerTransaction> erstellt.  
  
-   Der Designer wählt explizit Rückgängig-Komponenten, die entweder die standardmäßige Rückgängig-Komponente bereitgestellt, die von einer Implementierung der <xref:System.ComponentModel.Design.UndoEngine.UndoUnit>oder die Visual Studio-spezifische Implementierung <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>abgeleitet aus <xref:System.ComponentModel.Design.UndoEngine.UndoUnit>und stellt zudem eine Implementierung der beiden <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>und <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>.</xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> </xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> </xref:System.ComponentModel.Design.UndoEngine.UndoUnit> </xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> </xref:System.ComponentModel.Design.UndoEngine.UndoUnit> erstellen  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.ComponentModel.Design.UndoEngine></xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine></xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [Erweitern der Entwurfszeit-Unterstützung](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)

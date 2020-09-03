---
title: Bereitstellen von Rückgängigmachen für Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6136caaec0cb8f0d79e3fb7b96245fc3fd070710
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675341"
---
# <a name="supplying-undo-support-to-designers"></a>Bereitstellen von Rückgängig-Unterstützung für Designer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Designer, wie Editoren, müssen üblicherweise rückgängig-Vorgänge unterstützen, damit Benutzer ihre aktuellen Änderungen beim Ändern eines Code Elements umkehren können.  
  
 Die meisten in Visual Studio implementierten Designer verfügen über eine automatische Rückgängig-Unterstützung durch die Umgebung.  
  
 Designer Implementierungen, die Unterstützung für die Rückgängig-Funktion bereitstellen müssen:  
  
- Bereitstellen der rückgängig-Verwaltung durch Implementieren der abstrakten Basisklasse <xref:System.ComponentModel.Design.UndoEngine>  
  
- Unterstützung für Persistenz und CodeDom durch Implementieren der <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> -Klasse und der- <xref:System.ComponentModel.Design.IComponentChangeService> Klasse.  
  
  Weitere Informationen zum Schreiben von Designern mithilfe von [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] finden Sie [unter Erweitern der Entwurfszeit Unterstützung](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
  [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]Bietet eine standardmäßige rückgängig-Infrastruktur durch:  
  
- Bereitstellen von rückgängig-Verwaltungs Implementierungen durch die <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> Klassen und.  
  
- Bereitstellen von Persistenz und CodeDom-Unterstützung durch die Standard <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> -und- <xref:System.ComponentModel.Design.IComponentChangeService> Implementierungen  
  
## <a name="obtaining-undo-support-automatically"></a>Automatisches Abrufen der rückgängigunterstützung  
 Jeder in erstellte Designer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hat automatische und vollständige Rückgängig-Unterstützung, wenn, der Designer:  
  
- Verwendet eine- <xref:System.Windows.Forms.Control> basierte-Klasse für die Benutzeroberfläche.  
  
- Verwendet die CodeDom-basierte CodeDom-basierte Codegenerierung und das-Modell für die Codegenerierung und-Persistenz.  
  
     Weitere Informationen zum Arbeiten mit der CodeDom-Unterstützung in Visual Studio finden Sie unter generieren [und Kompilieren von dynamischem Quellcode](https://msdn.microsoft.com/library/d077a3e8-bd81-4bdf-b6a3-323857ea30fb) .  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>Verwendungszwecke des expliziten Designer Rückgängigmachen  
 Designer müssen eine eigene rückgängig-Verwaltung bereitstellen, wenn Sie eine grafische Benutzeroberfläche verwenden, die als Ansichts Adapter bezeichnet wird, und nicht die von bereitgestellte <xref:System.Windows.Forms.Control> .  
  
 Ein Beispiel hierfür ist das Erstellen eines Produkts mit einer webbasierten grafischen Entwurfs Schnittstelle anstelle einer [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] grafischen Benutzeroberfläche.  
  
 In solchen Fällen muss dieser Ansichts Adapter mithilfe von registriert [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute> werden, und es muss eine explizite rückgängig-Verwaltung bereitgestellt werden.  
  
 Designer müssen CodeDom-und persistenzunterstützung bereitstellen, wenn Sie nicht das [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Code Generierungs Modell verwenden, das im Namespace bereitgestellt wird <xref:System.CodeDom> .  
  
## <a name="undo-support-features-of-the-designer"></a>Rückgängig-Unterstützungsfunktionen des Designers  
 Das Environment SDK stellt Standard Implementierungen von Schnittstellen bereit, die zum Bereitstellen der Rückgängig-Unterstützung erforderlich sind, die von Designern verwendet werden kann, die keine- <xref:System.Windows.Forms.Control> basierten Klassen für Ihre Benutzeroberflächen oder das standardmäßige CodeDom und  
  
 Die- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> Klasse wird von der- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] <xref:System.ComponentModel.Design.UndoEngine> Klasse mithilfe einer Implementierung der- <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> Klasse zum Verwalten von rückgängig-Vorgängen abgeleitet.  
  
 Visual Studio stellt dem Designer die folgende Funktion zum Rückgängigmachen bereit:  
  
- Verknüpfte Rückgängig-Funktionalität über mehrere Designer hinweg.  
  
- Untergeordnete Einheiten innerhalb eines Designers können durch Implementieren von und in mit ihren übergeordneten Elementen interagieren <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> .  
  
  Das Environment SDK bietet CodeDom-und persistenzunterstützung durch Folgendes:  
  
- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> als Implementierungen von <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
  Eine, <xref:System.ComponentModel.Design.IComponentChangeService> die vom Entwurfs Host von bereitgestellt wird [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>Verwenden der Umgebungs-SDK-Features zum Bereitstellen von rückgängig  
 Zum Abrufen der Rückgängig-Unterstützung muss ein Objekt, das einen Designer implementiert, Folgendes  
  
- Instanziieren und initialisieren Sie eine Instanz der- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> Klasse mit einer gültigen- <xref:System.IServiceProvider> Implementierung.  
  
- Diese <xref:System.IServiceProvider> Klasse muss die folgenden Dienste bereitstellen:  
  
  - <xref:System.ComponentModel.Design.IDesignerHost>.  
  
  - <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
       Designer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , die die CodeDom-Serialisierung verwenden, wählen möglicherweise die Verwendung <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> von mit der [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] als-Implementierung von <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> .  
  
       In diesem Fall sollte die <xref:System.IServiceProvider> Klasse, die für den Konstruktor bereitgestellt wird, <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> dieses Objekt als Implementierung der-Klasse zurückgeben <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> .  
  
  - <xref:System.ComponentModel.Design.IComponentChangeService>  
  
       Designer, die den <xref:System.ComponentModel.Design.DesignSurface> vom Entwurfs Host bereitgestellten Standardwert verwenden [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , verfügen über eine Standard Implementierung der- <xref:System.ComponentModel.Design.IComponentChangeService> Klasse.  
  
  Designer, die einen basierten rückgängigmechanismus implementieren, verfolgen <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> Änderungen automatisch nach.  
  
- Eigenschafts Änderungen werden über das- <xref:System.ComponentModel.TypeDescriptor> Objekt vorgenommen.  
  
- <xref:System.ComponentModel.Design.IComponentChangeService> Ereignisse werden manuell generiert, wenn ein Commit für eine nicht behebbare Änderung ausgeführt wird.  
  
- Die Änderung des Designers wurde im Kontext eines erstellt <xref:System.ComponentModel.Design.DesignerTransaction> .  
  
- Der Designer wählt das explizite Erstellen von rückgängig-Einheiten mithilfe der standardmäßigen Rückgängig-Komponente aus, die von einer Implementierung von <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> oder der Visual Studio-spezifischen Implementierung bereitgestellt <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> wird. diese wird von abgeleitet <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> und stellt außerdem eine Implementierung von <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> und bereit <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> .  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [Erweitern der Entwurfszeitunterstützung](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)

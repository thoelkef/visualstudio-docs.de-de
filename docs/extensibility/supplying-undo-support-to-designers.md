---
title: Bereitstellen von Rückgängig-Unterstützung für Designer | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e243ccfc92c5e17dd25e6d77dede439daac08761
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747718"
---
# <a name="supply-undo-support-to-designers"></a>Bereitstellen von Rückgängig-Unterstützung für Designer

Designer, z. B. Editor, festzulegen, in der Regel Rückgängig-Vorgängen unterstützen müssen, damit Benutzer ihren letzten Änderungen umgekehrt werden können, wenn Sie ein Codeelement zu ändern.

Die meisten Designer in Visual Studio implementiert haben, "Rückgängigmachen von supportleistungen, die automatisch von der Umgebung".

Designer-Implementierungen, die für die Rückgängig-Funktion zu unterstützen:

- Bereitstellen von Rückgängig-Verwaltung durch die Implementierung der abstrakten Basisklasse <xref:System.ComponentModel.Design.UndoEngine>

- Geben Persistenz und CodeDOM-Unterstützung durch die Implementierung der <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> und <xref:System.ComponentModel.Design.IComponentChangeService> Klassen.

Weitere Informationen zum Schreiben von Designern mit .NET Framework finden Sie unter [Entwurfszeitunterstützung erweitern](/previous-versions/37899azc(v=vs.140)).

Die [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] bietet eine standardmäßige rückgängig-Infrastruktur durch:

- Bereitstellen von Rückgängig-Verwaltung-Implementierungen über die <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> und <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> Klassen.

- Angeben von Persistenz und CodeDOM-Unterstützung durch die Standardeinstellung <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> und <xref:System.ComponentModel.Design.IComponentChangeService> Implementierungen.

## <a name="obtain-undo-support-automatically"></a>Rückgängig-Unterstützung automatisch beziehen

Alle Designer in Visual Studio erstellt wurde, automatische und vollständige Rückgängig-Unterstützung If, den Designer:

- Verwendet eine <xref:System.Windows.Forms.Control> basierend-Klasse für die Benutzeroberfläche.

- Nutzt standard CodeDOM-basierten Code-Generierung und Analysesystem für die codegenerierung und Persistenz.

   Weitere Informationen zum Arbeiten mit Visual Studio CodeDOM-Unterstützung finden Sie unter [dynamische Quelle-Codegenerierung und-Kompilierung](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation).

## <a name="when-to-use-explicit-designer-undo-support"></a>Verwenden Sie explizite Designer Rückgängig-Unterstützung
 Designer müssen eigene rückgängig-Verwaltung angeben, wenn sie eine grafische Benutzeroberfläche, bezeichnet als Adapter anzeigen, als die vom verwenden <xref:System.Windows.Forms.Control>.

 Ein Beispiel hierfür kann ein Produkt mit einer .NET Framework-basierte grafische Benutzeroberfläche, anstatt eine Web-basierte grafische Entwurfsoberfläche erstellen.

 In solchen Fällen würden müssen diesen ansichtsadapters mit der Verwendung von Visual Studio registrieren <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>, und geben Sie explizite rückgängig-Verwaltung.

 Designer bereitstellen, CodeDOM und Persistenz unterstützen, wenn sie nicht zur Verfügung gestellt, Visual Studio Code-generierungsmodells verwenden müssen die <xref:System.CodeDom> Namespace.

## <a name="undo-support-features-of-the-designer"></a>Rückgängig für Unterstützungsfunktionen des Designers
 Das SDK-Umgebung stellt standardimplementierungen der Schnittstellen, die zu Rückgängig-Unterstützung, die von Designern, die nicht mit verwendet werden kann <xref:System.Windows.Forms.Control> basierende Klassen für ihren Benutzeroberflächen oder dem Standardmodell CodeDOM und Persistenz.

 Die <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> Klasse leitet sich von .NET Framework <xref:System.ComponentModel.Design.UndoEngine> Klasse mit einer Implementierung des der <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> Klasse zum Verwalten von Rückgängig-Vorgänge.

 Visual Studio bietet die folgenden Funktionen ab, der Designer Rückgängig:

- Verknüpften Rückgängig-Funktion über mehrere Designer.

- Untergeordnete Einheiten in einem Designer können mit ihren übergeordneten Elementen interagieren, durch die Implementierung <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> und <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> auf <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>.

Das SDK-Umgebung bietet CodeDOM und Persistenz durch Angabe:

- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> als eine Implementierung der <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

- Ein <xref:System.ComponentModel.Design.IComponentChangeService> vom Entwurfshost Visual Studio bereitgestellt.

## <a name="use-the-environment-sdk-features-to-supply-undo-support"></a>Verwenden Sie die Umgebung SDK-Funktionen zum Bereitstellen von Rückgängig-Unterstützung

Um Rückgängig-Unterstützung zu erhalten, muss ein Objekt, das Implementieren eines Designers instanziieren und initialisieren Sie eine Instanz von der <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> Klasse mit einer gültigen <xref:System.IServiceProvider> Implementierung. Dies <xref:System.IServiceProvider> Klasse muss die folgenden Dienste bereitstellen:

- <xref:System.ComponentModel.Design.IDesignerHost>.

- <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

   Designer, die mit Visual Studio CodeDOM-Serialisierung verwenden möchten <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> im Lieferumfang der [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] als eine Implementierung von der <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>.

   In diesem Fall die <xref:System.IServiceProvider> Klasse bereitgestellt, um die <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> Konstruktor muss dieses Objekt zurückgeben, wie eine Implementierung von der <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> Klasse.

- <xref:System.ComponentModel.Design.IComponentChangeService>

   Designer, die über das standardmäßige <xref:System.ComponentModel.Design.DesignSurface> bereitgestellt von der Visual Studio-Entwurf Host sind garantiert eine Standardimplementierung von der <xref:System.ComponentModel.Design.IComponentChangeService> Klasse.

Implementieren von Designern eine <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> basierend rückgängig-Mechanismus wird automatisch Änderungen nachverfolgt, wenn:

- Eigenschaftenänderungen erfolgen über die <xref:System.ComponentModel.TypeDescriptor> Objekt.

- <xref:System.ComponentModel.Design.IComponentChangeService> Ereignisse werden manuell generiert, wenn eine Änderung rückgängig zu machen, ein Commit ausgeführt wird.

- Änderung im Designer erstellt wurde, im Kontext einer <xref:System.ComponentModel.Design.DesignerTransaction>.

- Der Designer wählt explizit Rückgängig-Komponenten, die entweder die standardmäßige Rückgängig-Komponente, die durch eine Implementierung der bereitgestellten erstellen <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> oder die Visual Studio-spezifische Implementierung <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>, die sich daraus ableitet <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> und bietet außerdem eine Implementierung von sowohl <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> und <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>.

## <a name="see-also"></a>Siehe auch

- <xref:System.ComponentModel.Design.UndoEngine>
- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>
- [Erweitern der Entwurfszeitunterstützung](/previous-versions/37899azc(v=vs.140))
---
title: Bereitstellung von Undo-Support für Designer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0580f974c362a71c3e400946f2ad34f565ad1232
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699673"
---
# <a name="supply-undo-support-to-designers"></a>Bereitstellung von Undo-Unterstützung für Designer

Designer wie Editoren müssen in der Regel Rückgängig-Vorgänge unterstützen, damit Benutzer ihre letzten Änderungen beim Ändern eines Codeelements rückgängig machen können.

Die meisten in Visual Studio implementierten Designer unterstützen die Umgebung automatisch .

Designerimplementierungen, die Unterstützung für die Rückgängig-Funktion bereitstellen müssen:

- Rückgängig-Verwaltung durch Implementieren der abstrakten Basisklasse<xref:System.ComponentModel.Design.UndoEngine>

- Bereitstellen von Persistenz und <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> CodeDOM-Unterstützung durch Implementieren der und-Klassen. <xref:System.ComponentModel.Design.IComponentChangeService>

Weitere Informationen zum Schreiben von Designern mit .NET Framework finden Sie unter [Extend Design-Time Support](/previous-versions/37899azc(v=vs.140)).

Der [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] stellt eine standardmäßige Rückgängig-Infrastruktur bereit, indem:

- Bereitstellen von Undo-Management-Implementierungen über die <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> und-Klassen. <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>

- Bereitstellen von Persistenz und CodeDOM-Unterstützung durch die Standardeinstellung <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> und <xref:System.ComponentModel.Design.IComponentChangeService> Implementierungen.

## <a name="obtain-undo-support-automatically"></a>Automatischer Rückgängig-Support erhalten

Jeder Designer, der in Visual Studio erstellt wurde, bietet automatische und vollständige Rückgängig-Unterstützung, wenn der Designer:

- Verwendet eine <xref:System.Windows.Forms.Control> basierte Klasse für die Benutzeroberfläche.

- Verwendet standardmäßiges CodeDOM-basiertes Codegenerierungs- und Analysesystem für die Codegenerierung und Persistenz.

   Weitere Informationen zum Arbeiten mit Visual Studio CodeDOM-Unterstützung finden Sie unter [Dynamische Quellcodegenerierung und -kompilierung](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation).

## <a name="when-to-use-explicit-designer-undo-support"></a>Verwendung der Unterstützung für explizite Designer rückgängig machen
 Designer müssen ihre eigene Rückgängig-Verwaltung bereitstellen, wenn sie eine grafische Benutzeroberfläche verwenden, <xref:System.Windows.Forms.Control>die als Ansichtsadapter bezeichnet wird, die nicht von bereitgestellt wird.

 Ein Beispiel hierfür könnte das Erstellen eines Produkts mit einer webbasierten grafischen Entwurfsoberfläche anstelle einer .NET Framework-basierten grafischen Oberfläche sein.

 In solchen Fällen müsste dieser Ansichtsadapter mit <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>Visual Studio registriert und eine explizite Rückgängigverwaltung bereitstellen.

 Designer müssen CodeDOM- und Persistenzunterstützung bereitstellen, wenn sie das <xref:System.CodeDom> im Namensbereich bereitgestellte Visual Studio-Codegenerierungsmodell nicht verwenden.

## <a name="undo-support-features-of-the-designer"></a>Rückgängigmachen der Support-Funktionen des Designers
 Das Environment SDK stellt Standardimplementierungen von Schnittstellen bereit, die zum Bereitstellen <xref:System.Windows.Forms.Control> von Rückgängig-Unterstützung erforderlich sind und von Designern verwendet werden können, die keine basierten Klassen für ihre Benutzeroberflächen oder das Standardmäßige CodeDOM- und Persistenzmodell verwenden.

 Die <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> Klasse leitet sich von <xref:System.ComponentModel.Design.UndoEngine> der .NET Framework-Klasse ab, die eine Implementierung der <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> Klasse zum Verwalten von Rückgängig-Vorgängen verwendet.

 Visual Studio bietet die folgende Funktion zum Rückgängigmachen des Designers:

- Verknüpfte Rückgängig-Funktionalität für mehrere Designer.

- Untergeordnete Einheiten innerhalb eines Designers können <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> mit <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>ihren Eltern interagieren, indem sie implementieren und auf .

Das Environment SDK bietet CodeDOM- und Persistenzunterstützung, indem Folgendes zur Verfügung stellt:

- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>als Umsetzung der<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

- Eine <xref:System.ComponentModel.Design.IComponentChangeService> vom Visual Studio-Entwurfshost bereitgestellte.

## <a name="use-the-environment-sdk-features-to-supply-undo-support"></a>Verwenden der Umgebungs-SDK-Funktionen zum Bereitstellen von Rückgängig-Unterstützung

Um Rückgängig-Unterstützung zu erhalten, muss ein Objekt, das einen Designer <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> implementiert, <xref:System.IServiceProvider> eine Instanz der Klasse mit einer gültigen Implementierung instanziieren und initialisieren. Diese <xref:System.IServiceProvider> Klasse muss die folgenden Dienste bereitstellen:

- <xref:System.ComponentModel.Design.IDesignerHost>.

- <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

   Designer, die die Visual Studio CodeDOM-Serialisierung verwenden, können die mit der <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] als Implementierung der <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>bereitgestellte verwenden.

   In diesem Fall <xref:System.IServiceProvider> sollte die <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> dem Konstruktor bereitgestellte Klasse <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> dieses Objekt als Implementierung der Klasse zurückgeben.

- <xref:System.ComponentModel.Design.IComponentChangeService>

   Designer, die <xref:System.ComponentModel.Design.DesignSurface> die vom Visual Studio-Entwurfshost bereitgestellte Standardeinstellung verwenden, verfügen garantiert über eine Standardimplementierung der <xref:System.ComponentModel.Design.IComponentChangeService> Klasse.

Designer, <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> die einen basierten Rückgängig-Mechanismus implementieren, verfolgen Änderungen automatisch, wenn:

- Eigenschaftenänderungen werden über <xref:System.ComponentModel.TypeDescriptor> das Objekt vorgenommen.

- <xref:System.ComponentModel.Design.IComponentChangeService>Ereignisse werden manuell generiert, wenn eine rückgängig zu machende Änderung festgeschrieben wird.

- Die Änderung am Designer wurde im <xref:System.ComponentModel.Design.DesignerTransaction>Kontext einer erstellt.

- Der Designer wählt explizit Rückgängig-Einheiten mit der Standard-Rückgängig-Einheit <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> erstellen, die von <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>einer Implementierung einer <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> Implementierung oder der Visual <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>Studio-spezifischen Implementierung bereitgestellt wird, die von beiden und ermöglicht.

## <a name="see-also"></a>Weitere Informationen

- <xref:System.ComponentModel.Design.UndoEngine>
- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>
- [Erweitern sie den Design-Time-Support](/previous-versions/37899azc(v=vs.140))

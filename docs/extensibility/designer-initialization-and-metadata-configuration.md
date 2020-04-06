---
title: Designer-Initialisierung und Metadatenkonfiguration | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e876dd9e6fa95bbe180d1737bc8c4911f16e1e9a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712217"
---
# <a name="designer-initialization-and-metadata-configuration"></a>Designerinitialisierung und Metadatenkonfiguration

Die Manipulation der Metadaten und Filterattribute, die einer Designer- oder Designerkomponente zugeordnet sind, bietet <xref:System.Type> einen Mechanismus für Anwendungen, um zu definieren, welche Werkzeuge von einem bestimmten Designer verwendet werden, um verschiedene Objekte (z. B. Datenstrukturen, Klassen oder grafische Entitäten) zu behandeln, wenn der Designer verfügbar ist, und wie die Visual Studio-IDE für die Unterstützung des Designers konfiguriert ist (z. B. welche **Toolbox-Kategorie** oder Registerkarte verfügbar ist).

Der [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] bietet mehrere Mechanismen, um die Steuerung der Initialisierung einer Designer- oder Designerkomponente und die Manipulation ihrer Metadaten durch ein VSPackage zu erleichtern.

## <a name="initialize-metadata-and-configuration-information"></a>Initialisieren von Metadaten und Konfigurationsinformationen
 Da sie bei Bedarf geladen werden, wurde VSPackages möglicherweise nicht von der Visual Studio-Umgebung vor der Instanziierung eines Designers geladen. Daher kann VSPackages den Standardmechanismus zum Konfigurieren einer Designer- oder Designerkomponente bei der Erstellung nicht verwenden, d. h. zum Behandeln eines <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> Ereignisses. Stattdessen implementiert ein VSPackage eine <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> Instanz der Schnittstelle und registriert sich selbst, um Anpassungen bereitzustellen, die als Entwurfsoberflächenerweiterungen bezeichnet werden.

### <a name="customize-initialization"></a>Anpassen der Initialisierung

Das Anpassen eines Designers, einer Komponente oder einer Designeroberfläche umfasst Folgendes:

1. Ändern der Designermetadaten und effektives <xref:System.Type> Ändern des Zugriffs auf eine bestimmte oder konvertierte Datei.

    Dies geschieht in <xref:System.Drawing.Design.UITypeEditor> <xref:System.ComponentModel.TypeConverter> der Regel durch die oder Mechanismen.

    Wenn beispielsweise <xref:System.Windows.Forms>-basierte Designer initialisiert werden, ändert die <xref:System.Drawing.Design.UITypeEditor> Visual <xref:System.Web.UI.WebControls.Image> Studio-Umgebung die für Objekte, die mit dem Designer verwendet werden, um den Ressourcen-Manager zum Abrufen von Bitmaps anstelle des Dateisystems zu verwenden.

2. Integration in die Umgebung, z. B. durch Abonnieren von Ereignissen oder Abrufen von Projektkonfigurationsinformationen. Sie können Projektkonfigurationsinformationen abrufen und Ereignisse <xref:System.ComponentModel.Design.ITypeResolutionService> abonnieren, indem Sie die Schnittstelle abrufen.

3. Änderung der Benutzerumgebung durch Aktivieren geeigneter **Toolbox-Kategorien** oder Durch Einschränken der Anwendbarkeit des <xref:System.ComponentModel.ToolboxItemFilterAttribute> Designers durch Anwenden einer Instanz der Klasse auf den Designer.

### <a name="designer-initialization-by-a-vspackage"></a>Designerinitialisierung durch ein VSPackage

Ein VSPackage sollte die Designerinitialisierung behandeln, indem es:

1. Erstellen eines Objekts, das die <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> Klasse implementiert.

   > [!NOTE]
   > Die <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> Klasse sollte niemals für dasselbe <xref:Microsoft.VisualStudio.Shell.Package> Objekt wie die Klasse implementiert werden.

2. Registrieren der Klasse, <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> die implementiert wird, um Unterstützung für die Designererweiterungen des VSPackage bereitzustellen. Registrieren Sie die Klasse, <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute>indem <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> Sie Instanzen von <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>, und <xref:Microsoft.VisualStudio.Shell.Package>auf die Klasse anwenden, die die VSPackage-Implementierung von bereitstellt.

Wenn eine Designer- oder Designerkomponente erstellt wird, wird die Visual Studio-Umgebung:

- Greift auf jeden registrierten Entwurfsoberflächenerweiterungsanbieter zu.

- Instanziiert und initialisiert eine Instanz des Objekts <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> jedes Entwurfsoberflächenerweiterungsanbieters.

- Ruft die Methode oder <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> Methode des Entwurfsoberflächenerweiterungsanbieters auf (je nach Bedarf).

Beim Implementieren <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> des Objekts als Member eines VSPackage ist es wichtig, diefolgenden Zuverstehen:

- Die Visual Studio-Umgebung bietet keine Kontrolle darüber, welche `DesignSurfaceExtension` Metadaten oder andere Konfigurationseinstellungen die Änderungen eines bestimmten Anbieters vornehmen. Es ist möglich, `DesignSurfaceExtension` dass zwei oder mehr Anbieter dieselbe Designerfunktion auf widersprüchliche Weise ändern, wobei die endgültige Änderung endgültig ist. Es ist unbestimmt, welche Änderung zuletzt angewendet wird.

- Es ist möglich, eine Implementierung <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> des Objekts explizit auf <xref:System.ComponentModel.ToolboxItemFilterAttribute> bestimmte Designer zu beschränken, indem Instanzen von auf diese Implementierung angewendet werden. Weitere Informationen **zur** Toolbox-Elementfilterung finden Sie unter <xref:System.ComponentModel.ToolboxItemFilterAttribute> und <xref:System.ComponentModel.ToolboxItemFilterType>.

## <a name="additional-metadata-provisioning"></a>Zusätzliche Metadatenbereitstellung

Ein VSPackage kann die Konfiguration einer Designer- oder Designerkomponente ändern, die nicht zur Entwurfszeit ist.

Die <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> Klasse kann programmgesteuert verwendet oder auf ein VSPackage angewendet werden, das einen Designer bereitstellt.

Eine Instanz <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> der Klasse wird verwendet, um die Metadaten von Komponenten zu ändern, die auf einer Entwurfsoberfläche erstellt wurden. Beispielsweise könnte man einen Standardeigenschaftenbrowser, <xref:System.Windows.Forms.CommonDialog> der von Objekten verwendet wird, durch einen benutzerdefinierten Eigenschaftenbrowser ersetzen.

Änderungen, die von <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> einer Instanz bereitgestellt werden, <xref:Microsoft.VisualStudio.Shell.Package> die auf die Implementierung eines VSPackage angewendet wird, können einen von zwei Bereichen haben:

- Global -- für alle neuen Instanzen einer bestimmten Komponente

- Lokal - bezieht sich nur auf die Instanz der Komponente, die auf einer Entwurfsoberfläche erstellt wurde, die vom aktuellen VSPackage bereitgestellt wird.

Die `IsGlobal` Eigenschaft <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> der Instanz, die auf die <xref:Microsoft.VisualStudio.Shell.Package> Implementierung eines VSPackage angewendet wird, bestimmt diesen Bereich.

Durch Anwenden des Attributs <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> auf eine <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> Implementierung `true`von <xref:Microsoft.VisualStudio.Shell.Package> mit der Eigenschaft des Objekts, das wie unten festgelegt ist, wird der Browser für die gesamte Visual Studio-Umgebung geändert:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`

`internal class MyPackage : Package {}`

Wenn das globale Flag `false`auf festgelegt wurde, ist die Metadatenänderung lokal für den aktuellen Designer, der vom aktuellen VSPackage unterstützt wird:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`

`internal class MyPackage : Package {}`

> [!NOTE]
> Die Entwurfsoberfläche unterstützt nur das Erstellen von Komponenten, und daher können nur Komponenten über lokale Metadaten verfügen. Im obigen Beispiel haben wir versucht, eine Eigenschaft `Color` zu ändern, z. B. die Eigenschaft eines Objekts. Wenn `false` für das globale Flag `CustomBrowser` übergeben wurde, würde nie angezeigt `Color`werden, da der Designer nie tatsächlich eine Instanz von erstellt. Das Festlegen des `false` globalen Flags ist für Komponenten wie Steuerelemente, Timer und Dialogfelder nützlich.

## <a name="see-also"></a>Weitere Informationen

- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>
- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>
- <xref:System.ComponentModel.ToolboxItemFilterType>
- [Erweitern der Entwurfszeitunterstützung](https://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)

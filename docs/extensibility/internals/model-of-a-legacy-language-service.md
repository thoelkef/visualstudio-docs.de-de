---
title: Modell eines Legacy-Sprachdienstes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f024a02641902843f673ce3ff8583a4bce3b135
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707046"
---
# <a name="model-of-a-legacy-language-service"></a>Modell eines Legacysprachdiensts
Ein Sprachdienst definiert die Elemente und Features für eine bestimmte Sprache und wird verwendet, um dem Editor spezifische Informationen für diese Sprache bereitzustellen. Beispielsweise muss der Editor die Elemente und Schlüsselwörter der Sprache kennen, um die Syntaxfärbung zu unterstützen.

 Der Sprachdienst arbeitet eng mit dem vom Editor verwalteten Textpuffer und der Ansicht zusammen, die den Editor enthält. Die Microsoft IntelliSense **Quick Info-Option** ist ein Beispiel für eine Funktion, die von einem Sprachdienst bereitgestellt wird.

## <a name="a-minimal-language-service"></a>Ein minimaler Sprachdienst
 Der einfachste Sprachdienst enthält die folgenden beiden Objekte:

- Der *Sprachdienst* implementiert <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> die Schnittstelle. Ein Sprachdienst enthält Informationen über die Sprache, einschließlich des Namens, der Dateinamenerweiterungen, des Codefenster-Managers und des Colorizers.

- Der *Colorizer* implementiert <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> die Schnittstelle.

  Die folgende konzeptionelle Zeichnung zeigt ein Modell eines grundlegenden Sprachdienstes.

  ![Grafik "Sprachdienstmodell"](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel") Grundlegendes Sprachdienstmodell

  Das Dokumentfenster hostet die *Dokumentansicht* des [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Editors, in diesem Fall des Kerneditors. Die Dokumentansicht und der Textpuffer gehören dem Editor. Diese Objekte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] arbeiten mit durch ein spezielles Dokumentfenster, das als *Codefenster*bezeichnet wird. Das Codefenster ist <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> in einem Objekt enthalten, das von der IDE erstellt und gesteuert wird.

  Wenn eine Datei mit einer bestimmten Erweiterung geladen wird, sucht der Editor den Sprachdienst, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> der dieser Erweiterung zugeordnet ist, und übergibt ihm das Codefenster, indem er die Methode aufruft. Der Sprachdienst gibt einen *Codefenster-Manager*zurück, der die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> Schnittstelle implementiert.

  Die folgende Tabelle bietet einen Überblick über die Objekte im Modell.

| Komponente | Object | Funktion |
|------------------| - | - |
| Textpuffer | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> | Ein Unicode-Textstream zum Lesen/Schreiben. Es ist möglich, dass Text andere Codierungen verwendet. |
| Codefenster | <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> | Ein Dokumentfenster, das eine oder mehrere Textansichten enthält. Wenn [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sich das Codefenster im MDI-Modus (Multiple Document Interface) befindet, ist es ein untergeordnetes MDI-Fenster. |
| Textansicht | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> | Ein Fenster, in dem der Benutzer mithilfe von Tastatur und Maus navigieren und Text anzeigen kann. Eine Textansicht wird dem Benutzer als Editor angezeigt. Sie können Textansichten in normalen Editorfenstern, im Ausgabefenster und im Direktfenster verwenden. Darüber hinaus können Sie eine oder mehrere Textansichten in einem Codefenster konfigurieren. |
| Textmanager | Verwaltet vom <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> Dienst, von dem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> Sie einen Zeiger erhalten | Eine Komponente, die gemeinsame Informationen verwaltet, die von allen zuvor beschriebenen Komponenten gemeinsam genutzt werden. |
| Sprachdienst | Umsetzung abhängig; Implementiert<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> | Ein Objekt, das dem Editor sprachspezifische Informationen wie Syntaxhervorhebung, Anweisungsvervollständigung und Klammerabgleich bereitstellt. |

## <a name="see-also"></a>Weitere Informationen
- [Dokumentdaten und Dokumentansicht in benutzerdefinierten Editoren](../../extensibility/document-data-and-document-view-in-custom-editors.md)

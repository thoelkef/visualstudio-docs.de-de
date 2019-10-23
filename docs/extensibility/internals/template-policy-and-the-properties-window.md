---
title: Vorlagen Richtlinie und Eigenschaften Fenster | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e7135a7c99f1566eaacb4079e9787cf2b5606682
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722691"
---
# <a name="template-policy-and-the-properties-window"></a>Vorlagenrichtlinie und das Eigenschaftenfenster
Wenn ein Projekt in einem Enterprise-Vorlagen Projekt enthalten ist, kann dieses Enterprise-Vorlagen Projekt Richtlinien erzwingen. Die Vorlagen Richtlinie wird zu einem Einschränkungs System, das zum Festlegen von Standardwerten für Eigenschaften, zum Ausblenden von Eigenschaften, zum Hinzufügen von Eigenschaften usw. verwendet werden kann.

 Die Verwendung der Vorlagen Richtlinie zum Steuern der Anzeige von Informationen im **Eigenschaften** Fenster unterscheidet sich von der Implementierung <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> behandelt Objekteigenschaften auf Komponentenebene, während Vorlagen Richtlinien verwendet werden können, um Objekteigenschaften auf Projektmappen-oder Projektebene einzuschränken. Mit anderen Worten,

- Implementieren Sie die Methoden auf <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>, um zu bestimmen, was im **Eigenschaften** Fenster für bestimmte Objekte angezeigt wird.

- Verwenden Sie die Vorlagen Richtlinie auf Projektmappen-und Projektebene, um zu bestimmen, was im **Eigenschaften** Fenster für zuvor angegebene Objekte angezeigt wird.

  Die Verwendung der Vorlagen Richtlinie, um bestimmte Eigenschaften im **Eigenschaften** Fenster selektiv einzuschränken, wenn ein Projekt Element eines bestimmten Typs in **Projektmappen-Explorer** ausgewählt ist, kann für alle Mitglieder des Entwicklungsteams, die an einem Projekt arbeiten, von Vorteil sein. Beispielsweise können Sie mithilfe der Vorlagen Richtlinie alle Verbindungs Zeichenfolgen-Informationen in einer Datenbank für Ihre Entwickler einrichten und die Verbindungs Zeichenfolge als schreibgeschützt festlegen. Auf diese Weise können Sie eine einfache Möglichkeit bereitstellen, um sicherzustellen, dass jeder Entwickler den richtigen Pfad für den Datenzugriff verwendet.

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>
- [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md)
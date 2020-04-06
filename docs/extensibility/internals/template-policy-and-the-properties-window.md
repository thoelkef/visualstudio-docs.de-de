---
title: Vorlagenrichtlinie und das Eigenschaftenfenster | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 08ed6f416441d06767661e63b5e32454dbe07f93
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704668"
---
# <a name="template-policy-and-the-properties-window"></a>Vorlagenrichtlinie und das Eigenschaftenfenster
Wenn ein Projekt in einem Enterprise-Vorlagenprojekt enthalten ist, kann dieses Enterprise-Vorlagenprojekt Richtlinien erzwingen. Die Vorlagenrichtlinie wird zu einem einschränkenden System, das verwendet werden kann, um Standardwerte für Eigenschaften festzulegen, Eigenschaften auszublenden, Eigenschaften hinzuzufügen usw.

 Die Verwendung der Vorlagenrichtlinie zum Steuern der Anzeige <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>von Informationen im Fenster **Eigenschaften** unterscheidet sich von der Implementierung von . <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>behandelt Objekteigenschaften auf Komponentenebene, während die Vorlagenrichtlinie verwendet werden kann, um Objekteigenschaften auf Projektmappe- oder Projektebene einzuschränken. Mit anderen Worten,

- Implementieren Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> die Methoden, um zu bestimmen, was im **Eigenschaftenfenster** für bestimmte Objekte angezeigt wird.

- Verwenden von Vorlagenrichtlinien auf Projektmappen- und Projektebene, um zu bestimmen, was im **Eigenschaftenfenster** für zuvor angegebene Objekte angezeigt wird

  Die Verwendung der Vorlagenrichtlinie zum selektiven Einschränken bestimmter Eigenschaften im **Eigenschaftenfenster,** wenn ein Projektelement eines angegebenen Typs im **Projektmappen-Explorer** ausgewählt ist, kann für alle Mitglieder des Entwicklungsteams, die an einem Projekt arbeiten, von Vorteil sein. Mithilfe der Vorlagenrichtlinie können Sie beispielsweise alle Verbindungszeichenfolgeninformationen in einer Datenbank für Ihre Entwickler einrichten und die Verbindungszeichenfolge schreibgeschützt machen. Auf diese Weise können Sie eine einfache Möglichkeit bereitstellen, um sicherzustellen, dass jeder Entwickler den richtigen Pfad für den Datenzugriff verwendet.

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>
- [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md)

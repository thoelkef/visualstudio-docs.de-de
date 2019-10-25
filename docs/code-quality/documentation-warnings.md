---
title: Warnungen in der Dokumentation
ms.date: 09/16/2019
ms.topic: reference
f1_keywords:
- vs.codeanalysis.documentationrules
helpviewer_keywords:
- documentation warnings
- managed code analysis warnings, documentation warnings
- warnings, documentation
author: mavasani
ms.author: mavasani
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4946c69bbbe4bf1c240967ebd93ef58cfa79e333
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2019
ms.locfileid: "72807098"
---
# <a name="documentation-warnings"></a>Warnungen in der Dokumentation

Dokumentations Warnungen unterstützen das Schreiben von gut dokumentierten Bibliotheken durch die korrekte Verwendung von [XML-Dokumentations Kommentaren](/dotnet/csharp/codedoc) für extern sichtbare APIs.

## <a name="in-this-section"></a>In diesem Abschnitt

| Regel | Beschreibung |
| - | - |
| [CA1200: vermeiden Sie die Verwendung von-Endtags mit einem Präfix.](../code-quality/ca1200.md) | Das Attribut " [kref](/dotnet/csharp/programming-guide/xmldoc/cref-attribute) " in einem XML-Dokumenttag bedeutet "Code Verweis". Es gibt an, dass der innere Text des Tags ein Codeelement ist, wie z.B. ein Typ, eine Methode oder Eigenschaft. Vermeiden Sie die Verwendung von `cref`-Tags mit Präfixen, da der Compiler die Überprüfung von verweisen verhindert. Außerdem wird verhindert, dass die integrierte Entwicklungsumgebung (IDE) von Visual Studio diese Symbol Verweise bei refactoren findet und aktualisiert. |

## <a name="see-also"></a>Siehe auch

- [Code Analyse Warnungen](../code-quality/code-analysis-for-managed-code-warnings.md)

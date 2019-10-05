---
title: Dokumentations Warnungen
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
ms.openlocfilehash: 00b42dc20b228e30a9b2632a0525a1ec8a9ddbb1
ms.sourcegitcommit: 541a0556958201ad6626bc8638406ad02640f764
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/18/2019
ms.locfileid: "71079208"
---
# <a name="documentation-warnings"></a>Dokumentations Warnungen

Dokumentations Warnungen unterstützen das Schreiben von gut dokumentierten Bibliotheken durch die korrekte Verwendung von [XML-Dokumentations Kommentaren](https://docs.microsoft.com/dotnet/csharp/codedoc) für extern sichtbare APIs.

## <a name="in-this-section"></a>In diesem Abschnitt

| Regel | Beschreibung |
| - | - |
| [CA1200: Vermeiden Sie die Verwendung von-Endtags mit Präfix.](../code-quality/ca1200.md) | Das Attribut " [kref](https://docs.microsoft.com/dotnet/csharp/programming-guide/xmldoc/cref-attribute) " in einem XML-Dokumenttag bedeutet "Code Verweis". Es gibt an, dass der innere Text des Tags ein Codeelement ist, wie z.B. ein Typ, eine Methode oder Eigenschaft. Vermeiden Sie `cref` die Verwendung von Tags mit Präfixen, da dies verhindert, dass der Compiler Verweise überprüft. Außerdem wird verhindert, dass die integrierte Entwicklungsumgebung (IDE) von Visual Studio diese Symbol Verweise bei refactoren findet und aktualisiert. |

## <a name="see-also"></a>Siehe auch

- [Code Analyse Warnungen](../code-quality/code-analysis-for-managed-code-warnings.md)

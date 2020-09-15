---
title: Portabilität und Interoperabilitäts Warnungen
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Portablityrules
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis warnings, interoperability warnings, portability warnings
- portability warnings
- warnings, portability
- interoperability warnings
- warnings, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9f09ccafb79a87dff5c18bb4af11a12e1b1729a4
ms.sourcegitcommit: a18c7e9b367c2f92f6e54c3eaef442775d457667
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2020
ms.locfileid: "90100499"
---
# <a name="portability-and-interoperability-warnings"></a>Portabilität und Interoperabilitäts Warnungen

Portabilitäts Warnungen unterstützen Portabilität auf verschiedenen Plattformen Interoperabilitäts Warnungen unterstützen Interaktionen mit com-Clients.

## <a name="in-this-section"></a>In diesem Abschnitt

| Regel | Beschreibung |
| - | - |
| [CA1401: P/Aufrufe dürfen nicht sichtbar sein.](../code-quality/ca1401.md) | Eine öffentliche oder geschützte Methode in einem öffentlichen Typ weist das System.Runtime.InteropServices.DllImportAttribute-Attribut auf (wird auch vom Declare-Schlüsselwort in Visual Basic implementiert). Solche Methoden sollten nicht verfügbar gemacht werden. |
| [CA1416: Platt Form Kompatibilität überprüfen](../code-quality/ca1416.md) | Durch die Verwendung von Platt Form abhängigen APIs in einer Komponente wird der Code nicht mehr auf allen Plattformen funktionieren. |
| [CA1417: nicht `OutAttribute` für Zeichen folgen Parameter für P/Aufrufe verwenden](../code-quality/ca1417.md) | Zeichen folgen Parameter, die mit dem als Wert übermittelt werden, `OutAttribute` können die Laufzeit destabilisieren, wenn die Zeichenfolge eine Internpool vorhanden Zeichenfolge ist. |

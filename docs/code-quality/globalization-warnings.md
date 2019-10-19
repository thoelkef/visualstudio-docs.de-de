---
title: Globalisierungswarnungen
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.globalizationrules
helpviewer_keywords:
- warnings, globalization
- globalization warnings
- globalization [Visual Studio], warnings
- managed code analysis warnings, globalization warnings
ms.assetid: a8d12d41-14bf-4b43-af24-168312d7c390
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 11202e25dee89640c5a51450610919ad6a5c294c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649546"
---
# <a name="globalization-warnings"></a>Globalisierungswarnungen
Globalisierungs Warnungen unterstützen weltweit bereite Bibliotheken und Anwendungen.

## <a name="in-this-section"></a>In diesem Abschnitt

|Regel|Beschreibung|
|----------|-----------------|
|[CA1300: MessageBoxOptions angeben](../code-quality/ca1300.md)|Wenn in Kulturen, in denen von rechts nach links gelesen wird, ein Meldungsfeld richtig angezeigt werden soll, müssen der RightAlign-Member und der RtlReading-Member der MessageBoxOptions-Enumeration an die Show-Methode übergeben werden.|
|[CA1301: Doppelte Zugriffstasten vermeiden](../code-quality/ca1301.md)|Eine Zugriffstaste ermöglicht den Zugriff auf ein Steuerelement unter Verwendung der ALT-TASTE. Wenn mehrere Steuerelemente über doppelte Zugriffsschlüssel verfügen, ist das Verhalten des Zugriffsschlüssels nicht klar definiert.|
|[CA1302: Keine Hartkodierung für gebietsschemaspezifische Zeichenfolgen verwenden](../code-quality/ca1302.md)|Die System.Environment.SpecialFolder-Enumeration enthält Member, die auf besondere Systemordner verweisen. Die Speicherorte dieser Ordner können sich von Betriebssystem zu Betriebssystem unterscheiden. Der Benutzer kann einige Speicherorte ändern, und die Speicherorte sind lokalisiert. Die Environment. GetFolderPath-Methode gibt die Speicherorte zurück, die der Umgebung. SpecialFolder-Enumeration zugeordnet sind, lokalisiert und für den aktuell ausgeführten Computer geeignet ist.|
|[CA1303: Literale nicht als lokalisierte Parameter übergeben](../code-quality/ca1303.md)|Eine extern sichtbare Methode übergibt ein Zeichenfolgenliteralzeichen als Parameter an einen .net-Konstruktor oder eine Methode, und diese Zeichenfolge muss lokalisierbar sein.|
|[CA1304: CultureInfo angeben](../code-quality/ca1304.md)|Eine Methode oder ein Konstruktor ruft einen Member mit einer Überladung auf, die einen System.Globalization.CultureInfo-Parameter akzeptiert. Die Methode oder der Konstruktor ruft nicht die Überladung auf, die den CultureInfo-Parameter akzeptiert. Wenn ein CultureInfo-Objekt oder ein System.IFormatProvider-Objekt nicht angegeben wird, besitzt der vom überladenen Member bereitgestellte Standardwert möglicherweise nicht in allen Gebietsschemas den gewünschten Effekt.|
|[CA1305: IFormatProvider angeben](../code-quality/ca1305.md)|Eine Methode oder ein Konstruktor ruft einen oder mehrere Member auf, die Überladungen besitzen und einen System.IFormatProvider-Parameter akzeptieren; die Methode oder der Konstruktor ruft die Überladung nicht auf, die den IFormatProvider-Parameter akzeptiert. Wenn ein System.Globalization.CultureInfo-Objekt oder ein IFormatProvider-Objekt nicht angegeben wird, besitzt der vom überladenen Member bereitgestellte Standardwert möglicherweise nicht in allen Gebietsschemas den gewünschten Effekt.|
|[CA1306: Gebietsschema für Datentypen festlegen](../code-quality/ca1306.md)|Das Gebietsschema bestimmt kulturspezifische Darstellungselemente für Daten wie die für Zahlenwerte, Währungssymbole und Sortierreihenfolge verwendete Formatierung. Wenn Sie eine DataTable oder ein DataSet erstellen, sollten Sie das Gebietsschema explizit festlegen.|
|[CA1307: StringComparison angeben](../code-quality/ca1307.md)|Ein Zeichenfolgenvergleich verwendet eine Methodenüberladung, durch die kein StringComparison-Parameter festgelegt wird.|
|[CA1308: Zeichenfolgen in Großbuchstaben normalisieren](../code-quality/ca1308.md)|Zeichenfolgen sollten in Großschreibung normalisiert werden. Für eine kleine Gruppe von Zeichen wird bei der Konvertierung in Kleinbuchstaben kein Roundtrip ausgeführt.|
|[CA1309: Ordinal-StringComparison verwenden](../code-quality/ca1309.md)|Durch einen nicht linguistischen Zeichenfolgenvergleich wird der StringComparison-Parameter nicht auf Ordinal und nicht auf OrdinalIgnoreCase festgelegt. Wenn der Parameter explizit auf StringComparison.Ordinal oder StringComparison.OrdinalIgnoreCase festgelegt wird, werden die Codeausführung beschleunigt sowie Richtigkeit und Zuverlässigkeit gesteigert.|
|[CA2101: Marshalling für P-Invoke-Zeichenfolgenargumente festlegen](../code-quality/ca2101.md)|Ein Platt Form Aufruf-Member ermöglicht teilweise vertrauenswürdigen Aufrufern, verfügt über einen Zeichen folgen Parameter und führt die Zeichenfolge nicht explizit aus. Auf diese Weise kann potenziell eine Sicherheitslücke verursacht werden.|

---
title: Globalisierungswarnungen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.globalizationrules
helpviewer_keywords:
- warnings, globalization
- globalization warnings
- globalization [Visual Studio], warnings
- managed code analysis warnings, globalization warnings
ms.assetid: a8d12d41-14bf-4b43-af24-168312d7c390
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: aca9692b990df5b2612b04418729fec9cf59c256
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="globalization-warnings"></a>Globalisierungswarnungen
Globalisierungswarnungen Global verwendbare Bibliotheken und Anwendungen zu unterstützen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Regel|Beschreibung|  
|----------|-----------------|  
|[CA1300: MessageBoxOptions angeben](../code-quality/ca1300-specify-messageboxoptions.md)|Wenn in Kulturen, in denen von rechts nach links gelesen wird, ein Meldungsfeld richtig angezeigt werden soll, müssen der RightAlign-Member und der RtlReading-Member der MessageBoxOptions-Enumeration an die Show-Methode übergeben werden.|  
|[CA1301: Doppelte Zugriffstasten vermeiden](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Eine Zugriffstaste ermöglicht den Zugriff auf ein Steuerelement unter Verwendung der ALT-TASTE. Wenn mehrere Steuerelemente über doppelte Zugriffstasten verfügen, ist das Verhalten der Zugriffstaste nicht stringent.|  
|[CA1302: Keine Hartkodierung für gebietsschemaspezifische Zeichenfolgen verwenden](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|Die System.Environment.SpecialFolder-Enumeration enthält Member, die auf besondere Systemordner verweisen. Die Speicherorte dieser Ordner können sich von Betriebssystem zu Betriebssystem unterscheiden. Der Benutzer kann einige Speicherorte ändern, und die Speicherorte sind lokalisiert. Die Environment.GetFolderPath-Methode gibt die der Environment.SpecialFolder-Enumeration zugeordneten Speicherorte zurück, die lokalisiert und für den derzeit ausgeführten Computer geeignet sind.|  
|[CA1303: Literale nicht als lokalisierte Parameter übergeben](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Eine extern sichtbare Methode übergibt ein Zeichenfolgenliteral als Parameter an einen Konstruktor oder eine Methode in der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]-Klassenbibliothek, und diese Zeichenfolge sollte lokalisierbar sein.|  
|[CA1304: CultureInfo angeben](../code-quality/ca1304-specify-cultureinfo.md)|Eine Methode oder ein Konstruktor ruft einen Member mit einer Überladung auf, die einen System.Globalization.CultureInfo-Parameter akzeptiert. Die Methode oder der Konstruktor ruft nicht die Überladung auf, die den CultureInfo-Parameter akzeptiert. Wenn ein CultureInfo-Objekt oder ein System.IFormatProvider-Objekt nicht angegeben wird, besitzt der vom überladenen Member bereitgestellte Standardwert möglicherweise nicht in allen Gebietsschemas den gewünschten Effekt.|  
|[CA1305: IFormatProvider angeben](../code-quality/ca1305-specify-iformatprovider.md)|Eine Methode oder ein Konstruktor ruft einen oder mehrere Member auf, die Überladungen besitzen und einen System.IFormatProvider-Parameter akzeptieren; die Methode oder der Konstruktor ruft die Überladung nicht auf, die den IFormatProvider-Parameter akzeptiert. Wenn ein System.Globalization.CultureInfo-Objekt oder ein IFormatProvider-Objekt nicht angegeben wird, besitzt der vom überladenen Member bereitgestellte Standardwert möglicherweise nicht in allen Gebietsschemas den gewünschten Effekt.|  
|[CA1306: Gebietsschema für Datentypen festlegen](../code-quality/ca1306-set-locale-for-data-types.md)|Das Gebietsschema bestimmt kulturspezifische Darstellungselemente für Daten wie die für Zahlenwerte, Währungssymbole und Sortierreihenfolge verwendete Formatierung. Wenn Sie eine DataTable oder ein DataSet erstellen, sollten Sie das Gebietsschema explizit festlegen.|  
|[CA1307: StringComparison angeben](../code-quality/ca1307-specify-stringcomparison.md)|Ein Zeichenfolgenvergleich verwendet eine Methodenüberladung, durch die kein StringComparison-Parameter festgelegt wird.|  
|[CA1308: Zeichenfolgen in Großbuchstaben normalisieren](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Zeichenfolgen sollten in Großschreibung normalisiert werden. Für eine kleine Gruppe von Zeichen wird bei der Konvertierung in Kleinbuchstaben kein Roundtrip ausgeführt.|  
|[CA1309: Ordinal-StringComparison verwenden](../code-quality/ca1309-use-ordinal-stringcomparison.md)|Durch einen nicht linguistischen Zeichenfolgenvergleich wird der StringComparison-Parameter nicht auf Ordinal und nicht auf OrdinalIgnoreCase festgelegt. Wenn der Parameter explizit auf StringComparison.Ordinal oder StringComparison.OrdinalIgnoreCase festgelegt wird, werden die Codeausführung beschleunigt sowie Richtigkeit und Zuverlässigkeit gesteigert.|  
|[: Ca2101 Marshalling für P/Invoke-Zeichenfolgenargumente festlegen](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Ein Plattformaufruf Plattformaufrufmember lässt teilweise vertrauenswürdige Aufrufer zu, enthält einen Zeichenfolgenparameter und führt kein explizites Marshalling die Zeichenfolge. Auf diese Weise kann potenziell eine Sicherheitslücke verursacht werden.|
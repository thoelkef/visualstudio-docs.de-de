---
title: Eigenschaften von Domäneneigenschaften
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain properties
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: debf263fa18d2a6af8e95ee959002686540e2c06
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658201"
---
# <a name="properties-of-domain-properties"></a>Eigenschaften von Domäneneigenschaften
Eine *Domänen Eigenschaft* ist eine Funktion eines Modell Elements, das einen Wert enthalten kann. So kann die Domänenklasse `Person` beispielsweise die Eigenschaften `Name` und `BirthDate` aufweisen. In der DSL-Definition werden die Domäneneigenschaften im Domänenklassenfeld im Diagramm und unter der Domänenklasse im DSL-Explorer aufgelistet. Weitere Informationen finden Sie unter [Definieren einer domänenspezifischen Sprache](../modeling/how-to-define-a-domain-specific-language.md).

> [!NOTE]
> Der Begriff "Eigenschaft" umfasst zwei Verwendungen. Eine *Domänen Eigenschaft* ist ein Feature, das Sie für eine Domänen Klasse definieren. Im Gegensatz dazu verfügen viele Elemente einer DSL über *Eigenschaften*, die im Fenster **Eigenschaften** in der DSL-Definition aufgeführt sind. Jede Domäneneigenschaft besitzt beispielsweise einen Satz von Eigenschaften, die im vorliegenden Thema beschrieben werden.

 Wenn ein Benutzer während der Laufzeit Instanzen der Domänenklasse erstellt, können die Werte der Domäneneigenschaften im Eigenschaftenfenster betrachtet und auf den Formen dargestellt werden.

 Die meisten Domäneneigenschaften werden als gewöhnliche CLR-Eigenschaften implementiert. Vom Standpunkt der Programmierung aus betrachtet besitzen Domäneneigenschaften jedoch eine reichhaltigere Funktionalität als gewöhnliche Programmeigenschaften:

- Sie können Regeln und Ereignisse definieren, welche den Zustand einer Eigenschaft überwachen. Weitere Informationen finden Sie unter [reagieren auf und](../modeling/responding-to-and-propagating-changes.md)weitergeben von Änderungen.

- Transaktionen tragen dazu bei, dass inkonsistenten Zuständen vorgebeugt wird. Weitere Informationen finden Sie unter [navigieren und Aktualisieren eines Modells im Programm Code](../modeling/navigating-and-updating-a-model-in-program-code.md).

  Wenn Sie eine Domäneneigenschaft in einem Diagramm oder im DSL-Explorer auswählen, werden die folgenden Elemente im Eigenschaftenfenster angezeigt. Weitere Informationen zur Verwendung dieser Elemente finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

|property|Beschreibung|Standardwert|
|-|-|-|
|**Beschreibung**|Die Beschreibung, die zum Dokumentieren der Benutzeroberfläche (UI) des generierten Designers verwendet wird.|\<none>|
|**Anzeige Name**|Der Name, der im generierten Designer für diese Domäneneigenschaft angezeigt wird. Dieser kann Leer- und Satzzeichen enthalten, z. B. "Titel des Songs".|\<none>|
|**Element Namen Anbieter**|Dieser ist nur dann anwendbar, wenn Sie `Is Element Name` auf `true` eingestellt haben. Sie können Code schreiben, der einen Namen für ein neues Element einer Domänenklasse bereitstellt. Dabei wird das Standardverhalten überschrieben.<br /><br /> Erstellen Sie in einer Codedatei im DSL-Projekt eine Klasse, die vom <xref:Microsoft.VisualStudio.Modeling.ElementNameProvider> abgeleitet wird.<br /><br /> Klicken Sie dann im DSL-Explorer mit der rechten Maustaste auf den Stamm der DSL. Klicken Sie danach auf "Externen Typ hinzufügen". Geben Sie den Namen der Klasse ein.<br /><br /> Wählen Sie diese Domäneneigenschaft erneut aus. Wählen Sie dann den Namen der Klasse in der Dropdownliste aus.|\<none>|
|**Getter Access-Modifizierer**|Die Zugriffsebene der Domänenklasse (`public` oder `internal`). Diese steuert den Umfang, in welchem der Programmcode auf die Eigenschaft zugreifen kann.|`public`|
|**Hilfe Schlüsselwort**|Das optionale Schlüsselwort, das zum Indizieren der F1-Hilfe für diese Domäneneigenschaft verwendet wird.|\<none>|
|**Kann durchsucht werden**|Falls `True` gilt, wird die Domäneneigenschaft für den Benutzer im Eigenschaftenfenster angezeigt, sofern Modelle dieser DSL geöffnet sind.<br /><br /> Falls `False` gilt, wird die Domäneneigenschaft auf der Benutzeroberfläche (UI) ausgeblendet.<br /><br /> Wenn Sie die Domänen Eigenschaft sichtbar machen möchten, aber schreibgeschützt ist, legen Sie **für Benutzeroberfläche**schreibgeschützt fest.|`True`|
|**Ist Element Name**|Falls `True` gilt, wird diese Domäneneigenschaft als Name ihres Modellelements im DSL-Explorer angezeigt.<br /><br /> Neue Modellelemente erhalten für diese Eigenschaft einen eindeutigen Standardwert. Wenn Sie steuern möchten, wie diese Werte generiert werden, legen Sie **Element Namen Anbieter**fest.|`False`|
|**Ist UI-schreibgeschützt**|Falls `True` gilt, kann der Wert der Domäneneigenschaft nicht mit der Benutzeroberfläche geändert werden. Er kann weiterhin durch die Programme festgelegt werden, und er wird im Eigenschaftenfenster angezeigt.<br /><br /> Wenn Sie die Domänen Eigenschaft für den Benutzer ausblenden möchten **, legen Sie**durchsuchbar fest. Wenn Sie den Zugriff nach Programmen steuern möchten, legen Sie **Setter-Zugriffsmodifizierer**fest.|`False`|
|**Art**|Die Art der Domäneneigenschaft (`Normal`, `Calculated` oder `CustomStorage`). Weitere Informationen finden Sie unter [berechnete und benutzerdefinierte Speicher Eigenschaften](../modeling/calculated-and-custom-storage-properties.md).|`Normal`|
|**Name**|Der Name dieser Domäneneigenschaft. Dies muss ein gültiger Bezeichner sein, z. b. " **songtitle**".|\<none>|
|**Notizen**|Informelle Hinweise, die mit dieser Domäneneigenschaft verknüpft sind.|\<none>|
|**Setter**|Der Zugriffsmodifizierer für den Setter. Dieser steuert den Umfang, in welchem der Programmcode die Eigenschaft festlegen kann.|`public`|
|**Type**|Der Typ der Eigenschaft. Um die Liste der verfügbaren Typen hinzuzufügen, klicken Sie mit der rechten Maustaste auf den Stamm der DSL im DSL-Explorer, und klicken Sie dann auf **externen Typ hinzufügen**.|`String`|

## <a name="see-also"></a>Siehe auch

- [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
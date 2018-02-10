---
title: "Eigenschaften von Domäneneigenschaften | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, domain properties
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 7d964eb9f0dcabdb8050074121d094245aca9bb7
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="properties-of-domain-properties"></a>Eigenschaften von Domäneneigenschaften
Ein *Eigenschaft "Domain"* ist ein Feature von einem Modellelement, das einen Wert enthalten darf. So kann die Domänenklasse `Person` beispielsweise die Eigenschaften `Name` und `BirthDate` aufweisen. In der DSL-Definition werden die Domäneneigenschaften im Domänenklassenfeld im Diagramm und unter der Domänenklasse im DSL-Explorer aufgelistet. Weitere Informationen finden Sie unter [zum Definieren einer domänenspezifischen Sprache](../modeling/how-to-define-a-domain-specific-language.md).  
  
> [!NOTE]
>  Der Begriff "Eigenschaft" umfasst zwei Verwendungen. Ein *Eigenschaft "Domain"* ist eine Funktion, die Sie für eine Domänenklasse definieren. Viele Elemente von einem DSL, im Gegensatz dazu haben *Eigenschaften*, die aufgeführt sind, der **Eigenschaften** Fenster in der DSL-Definition. Jede Domäneneigenschaft besitzt beispielsweise einen Satz von Eigenschaften, die im vorliegenden Thema beschrieben werden.  
  
 Wenn ein Benutzer während der Laufzeit Instanzen der Domänenklasse erstellt, können die Werte der Domäneneigenschaften im Eigenschaftenfenster betrachtet und auf den Formen dargestellt werden.  
  
 Die meisten Domäneneigenschaften werden als gewöhnliche CLR-Eigenschaften implementiert. Vom Standpunkt der Programmierung aus betrachtet besitzen Domäneneigenschaften jedoch eine reichhaltigere Funktionalität als gewöhnliche Programmeigenschaften:  
  
-   Sie können Regeln und Ereignisse definieren, welche den Zustand einer Eigenschaft überwachen. Weitere Informationen finden Sie unter [Weitergeben von Änderungen und reagieren auf](../modeling/responding-to-and-propagating-changes.md).  
  
-   Transaktionen tragen dazu bei, dass inkonsistenten Zuständen vorgebeugt wird. Weitere Informationen finden Sie unter [Navigieren in und Aktualisieren eines Modells im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
 Wenn Sie eine Domäneneigenschaft in einem Diagramm oder im DSL-Explorer auswählen, werden die folgenden Elemente im Eigenschaftenfenster angezeigt. Weitere Informationen zur Verwendung dieser Elemente finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Eigenschaft|Beschreibung|Standardwert|  
|--------------|-----------------|-------------------|  
|**Beschreibung**|Die Beschreibung, die zum Dokumentieren der Benutzeroberfläche (UI) des generierten Designers verwendet wird.|\<keine >|  
|**Anzeigename**|Der Name, der im generierten Designer für diese Domäneneigenschaft angezeigt wird. Dieser kann Leer- und Satzzeichen enthalten, z. B. "Titel des Songs".|\<keine >|  
|**Element Name-Anbieter**|Dieser ist nur dann anwendbar, wenn Sie `Is Element Name` auf `true` eingestellt haben. Sie können Code schreiben, der einen Namen für ein neues Element einer Domänenklasse bereitstellt. Dabei wird das Standardverhalten überschrieben.<br /><br /> Erstellen Sie in einer Codedatei im DSL-Projekt eine Klasse, die vom <xref:Microsoft.VisualStudio.Modeling.ElementNameProvider> abgeleitet wird.<br /><br /> Klicken Sie dann im DSL-Explorer mit der rechten Maustaste auf den Stamm der DSL. Klicken Sie danach auf "Externen Typ hinzufügen". Geben Sie den Namen der Klasse ein.<br /><br /> Wählen Sie diese Domäneneigenschaft erneut aus. Wählen Sie dann den Namen der Klasse in der Dropdownliste aus.|\<keine >|  
|**Getter-Zugriffsmodifizierer**|Die Zugriffsebene der Domänenklasse (`public` oder `internal`). Diese steuert den Umfang, in welchem der Programmcode auf die Eigenschaft zugreifen kann.|`public`|  
|**Schlüsselwort "Help"**|Das optionale Schlüsselwort, das zum Indizieren der F1-Hilfe für diese Domäneneigenschaft verwendet wird.|\<keine >|  
|**Wird durchsucht werden kann**|Falls `True` gilt, wird die Domäneneigenschaft für den Benutzer im Eigenschaftenfenster angezeigt, sofern Modelle dieser DSL geöffnet sind.<br /><br /> Falls `False` gilt, wird die Domäneneigenschaft auf der Benutzeroberfläche (UI) ausgeblendet.<br /><br /> Wenn Sie die Eigenschaft "Domain" sichtbar, sind jedoch schreibgeschützt machen möchten, legen Sie **ist UI Read Only**.|`True`|  
|**Elementname ist**|Falls `True` gilt, wird diese Domäneneigenschaft als Name ihres Modellelements im DSL-Explorer angezeigt.<br /><br /> Neue Modellelemente erhalten für diese Eigenschaft einen eindeutigen Standardwert. Wenn Sie möchten steuern, wie diese Werte generiert werden, legen Sie **Element Namensdienstanbieter**.|`False`|  
|**Benutzeroberfläche werden nur gelesen werden**|Falls `True` gilt, kann der Wert der Domäneneigenschaft nicht mit der Benutzeroberfläche geändert werden. Er kann weiterhin durch die Programme festgelegt werden, und er wird im Eigenschaftenfenster angezeigt.<br /><br /> Wenn Sie die Eigenschaft "Domain" vom Benutzer ausblenden möchten, legen Sie **durchsuchbar ist**. Wenn Sie den Zugriff von Programmen steuern möchten, legen Sie **Setter Zugriffsmodifizierer**.|`False`|  
|**Kind**|Die Art der Domäneneigenschaft (`Normal`, `Calculated` oder `CustomStorage`). Weitere Informationen finden Sie unter [berechnet und benutzerdefinierte Speichereigenschaften](../modeling/calculated-and-custom-storage-properties.md).|`Normal`|  
|**Name**|Der Name dieser Domäneneigenschaft. Es muss ein gültiger Bezeichner, z. B. **SongTitle**.|\<keine >|  
|**Notizen**|Informelle Hinweise, die mit dieser Domäneneigenschaft verknüpft sind.|\<keine >|  
|**Setter-Zugriffsmodifizierer**|Der Zugriffsmodifizierer für den Setter. Dieser steuert den Umfang, in welchem der Programmcode die Eigenschaft festlegen kann.|`public`|  
|**Type**|Der Typ der Eigenschaft. Um die Liste der verfügbaren Typen hinzuzufügen, mit der rechten Maustaste in des Stamm der DSL im DSL-Explorer, und klicken Sie auf **Hinzufügen externer Typ**.|`String`|  
  
## <a name="see-also"></a>Siehe auch  
 [Domänenspezifische Sprache Tools Glossar](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
---
title: "Eigenschaften von Dom&#228;neneigenschaften | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Domänenspezifische Sprache, Domäneneigenschaften"
ms.assetid: a9471562-d6f2-46bf-9872-e0d66ba03150
caps.latest.revision: 24
caps.handback.revision: 24
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Eigenschaften von Dom&#228;neneigenschaften
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Eine *Domäneneigenschaft* stellt die Funktion eines Modellelements dar, welches einen Wert enthalten kann.  So kann die Domänenklasse `Person` beispielsweise die Eigenschaften `Name` und `BirthDate` aufweisen.  In der DSL\-Definition werden die Domäneneigenschaften im Domänenklassenfeld im Diagramm und unter der Domänenklasse im DSL\-Explorer aufgelistet.  Weitere Informationen finden Sie unter [So definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md).  
  
> [!NOTE]
>  Der Begriff "Eigenschaft" umfasst zwei Verwendungen.  Eine *Domäneneigenschaft* stellt eine Funktion dar, die Sie in einer Domänenklasse definieren.  Im Gegensatz dazu besitzen viele Elemente einer DSL jene *Eigenschaften*, die im Fenster **Eigenschaften** in der DSL\-Definition aufgelistet sind.  Jede Domäneneigenschaft besitzt beispielsweise einen Satz von Eigenschaften, die im vorliegenden Thema beschrieben werden.  
  
 Wenn ein Benutzer während der Laufzeit Instanzen der Domänenklasse erstellt, können die Werte der Domäneneigenschaften im Eigenschaftenfenster betrachtet und auf den Formen dargestellt werden.  
  
 Die meisten Domäneneigenschaften werden als gewöhnliche CLR\-Eigenschaften implementiert.  Vom Standpunkt der Programmierung aus betrachtet besitzen Domäneneigenschaften jedoch eine reichhaltigere Funktionalität als gewöhnliche Programmeigenschaften:  
  
-   Sie können Regeln und Ereignisse definieren, welche den Zustand einer Eigenschaft überwachen.  Weitere Informationen finden Sie unter [Reagieren auf und Propagieren von Änderungen](../modeling/responding-to-and-propagating-changes.md).  
  
-   Transaktionen tragen dazu bei, dass inkonsistenten Zuständen vorgebeugt wird.  Weitere Informationen finden Sie unter [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
 Wenn Sie eine Domäneneigenschaft in einem Diagramm oder im DSL\-Explorer auswählen, werden die folgenden Elemente im Eigenschaftenfenster angezeigt.  Weitere Informationen zum Verwenden dieser Elemente finden Sie unter [Anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Eigenschaft|Beschreibung|Standardwert|  
|-----------------|------------------|------------------|  
|**Beschreibung**|Die Beschreibung, die zum Dokumentieren der Benutzeroberfläche \(UI\) des generierten Designers verwendet wird.|\<Keine\>|  
|**Angezeigter Name**|Der Name, der im generierten Designer für diese Domäneneigenschaft angezeigt wird.  Dieser kann Leer\- und Satzzeichen enthalten, z. B. "Titel des Songs".|\<Keine\>|  
|**Elementnamenanbieter**|Dieser ist nur dann anwendbar, wenn Sie `Is Element Name` auf `true` eingestellt haben.  Sie können Code schreiben, der einen Namen für ein neues Element einer Domänenklasse bereitstellt. Dabei wird das Standardverhalten überschrieben.<br /><br /> Erstellen Sie in einer Codedatei im DSL\-Projekt eine Klasse, die vom <xref:Microsoft.VisualStudio.Modeling.ElementNameProvider> abgeleitet wird.<br /><br /> Klicken Sie dann im DSL\-Explorer mit der rechten Maustaste auf den Stamm der DSL. Klicken Sie danach auf "Externen Typ hinzufügen".  Geben Sie den Namen der Klasse ein.<br /><br /> Wählen Sie diese Domäneneigenschaft erneut aus. Wählen Sie dann den Namen der Klasse in der Dropdownliste aus.|\<Keine\>|  
|**Getter\-Zugriffsmodifizierer**|Die Zugriffsebene der Domänenklasse \(`public` oder `internal`\).  Diese steuert den Umfang, in welchem der Programmcode auf die Eigenschaft zugreifen kann.|`public`|  
|**Hilfsschlüsselwort**|Das optionale Schlüsselwort, das zum Indizieren der F1\-Hilfe für diese Domäneneigenschaft verwendet wird.|\<Keine\>|  
|**Kann durchsucht werden**|Falls `True` gilt, wird die Domäneneigenschaft für den Benutzer im Eigenschaftenfenster angezeigt, sofern Modelle dieser DSL geöffnet sind.<br /><br /> Falls `False` gilt, wird die Domäneneigenschaft auf der Benutzeroberfläche \(UI\) ausgeblendet.<br /><br /> Wenn die Domäneneigenschaft sichtbar und zugleich schreibgeschützt sein soll, stellen Sie **Ist UI\-schreibgeschützt** ein.|`True`|  
|**Ist Elementname**|Falls `True` gilt, wird diese Domäneneigenschaft als Name ihres Modellelements im DSL\-Explorer angezeigt.<br /><br /> Neue Modellelemente erhalten für diese Eigenschaft einen eindeutigen Standardwert.  Wenn Sie die Art und Weise steuern möchten, in der diese Werte generiert werden, stellen Sie **Elementnamenanbieter** ein.|`False`|  
|**Ist UI\-schreibgeschützt**|Falls `True` gilt, kann der Wert der Domäneneigenschaft nicht mit der Benutzeroberfläche geändert werden.  Er kann weiterhin durch die Programme festgelegt werden, und er wird im Eigenschaftenfenster angezeigt.<br /><br /> Wenn Sie die Domäneneigenschaft für den Benutzer ausblenden möchten, stellen Sie **Kann durchsucht werden** ein.  Wenn Sie den Zugriff über die Programme steuern möchten, stellen Sie **Setter\-Zugriffsmodifizierer** ein.|`False`|  
|**Art**|Die Art der Domäneneigenschaft \(`Normal`, `Calculated` oder `CustomStorage`\).  Weitere Informationen finden Sie unter [Berechnete und benutzerdefinierte Speichereigenschaften](../modeling/calculated-and-custom-storage-properties.md).|`Normal`|  
|**Name**|Der Name dieser Domäneneigenschaft.  Dieser muss ein gültiger Bezeichner sein, z. B. "SongTitle".|\<Keine\>|  
|**Hinweise**|Informelle Hinweise, die mit dieser Domäneneigenschaft verknüpft sind.|\<Keine\>|  
|**Setter\-Zugriffsmodifizierer**|Der Zugriffsmodifizierer für den Setter.  Dieser steuert den Umfang, in welchem der Programmcode die Eigenschaft festlegen kann.|`public`|  
|**Typ**|Der Typ der Eigenschaft.  Zum Hinzufügen zur Liste der verfügbaren Typen klicken Sie mit der rechten Maustaste auf den Stamm der DSL im DSL\-Explorer. Klicken Sie dann auf **Externen Typ hinzufügen**.|`String`|  
  
## Siehe auch  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/de-de/ca5e84cb-a315-465c-be24-76aa3df276aa)
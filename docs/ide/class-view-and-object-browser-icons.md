---
title: "Symbole in der Klassenansicht und im Objektbrowser | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Symbole, im Objektkatalog"
  - "Signalsymbole"
  - "Klassenansicht (Tool), Symbole"
  - "Grafische Symbole"
  - "IntelliSense, Symbole"
  - "Symbole, IntelliSense"
  - "Symbole, Symbole im Objektkatalog"
  - "Objektkatalog, Symbole in der Klassenansicht"
ms.assetid: 58cc3f44-c296-4a88-a008-09d28598d9c0
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Symbole in der Klassenansicht und im Objektbrowser
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die **Klassenansicht** und der **Objektkatalog** enthalten eine Reihe von Symbolen, die Codeentitäten darstellen, z. B. Namespaces, Klassen, Funktionen oder Variablen.  In der folgenden Tabelle werden die Symbole verdeutlicht und beschrieben.  
  
|Symbol|Beschreibung|Symbol|Beschreibung|  
|------------|------------------|------------|------------------|  
|![Symbol "Namespace"](~/docs/ide/media/vxnamespace_icon.gif "vxNamespace\_Icon")|Namespace|![Symbol "Deklaration"](~/docs/ide/media/vxmethod_icon.gif "vxMethod\_Icon")|Methode oder Funktion|  
|![Symbol "Klasse"](~/docs/ide/media/vxclass_icon.gif "vxClass\_Icon")|Klasse|![Symbol "Operator"](~/docs/ide/media/vxoperator_icon.gif "vxOperator\_Icon")|Operator|  
|![Schnittstellensymbol "Lollipop"](~/docs/ide/media/vxinterface_icon.gif "vxInterface\_Icon")|Schnittstelle|![Symbol "Eigenschaften"](~/docs/ide/media/vxproperty_icon.gif "vxProperty\_Icon")|Eigenschaft|  
|![Symbol "Struktur"](~/docs/ide/media/vxstruct_icon.gif "vxStruct\_Icon")|Struktur|![Symbol "Feld"](~/docs/ide/media/vxfield_icon.gif "vxField\_Icon")|Feld oder Variable|  
|![Symbol "Union"](~/docs/ide/media/vxunion_icon.gif "vxUnion\_Icon")|Union|![Symbol "Ereignis"](~/docs/ide/media/vxevent_icon.gif "vxEvent\_Icon")|Ereignis|  
|![Symbol "Enumeration"](~/docs/ide/media/vxenum_icon.gif "vxEnum\_Icon")|Enum|![Symbol "Konstante"](~/docs/ide/media/vxconstant_icon.gif "vxConstant\_Icon")|Konstante|  
|![Symbol "Typdefinition"](~/docs/ide/media/vxtypedef_icon.gif "vxTypeDef\_Icon")|TypeDef|![Symbol "Element enumerieren"](~/docs/ide/media/vxenumitem_icon.gif "vxEnumItem\_Icon")|Enumerationselement|  
|![Symbol "Visual Studio&#45;Modul"](~/docs/ide/media/vxmodule_icon.gif "vxModule\_Icon")|Modul|![Symbol "Zuordnungselement"](~/docs/ide/media/vxmapitem_icon.gif "vxMapItem\_Icon")|Zuordnungselement|  
|![Symbol "Erweiterungsmethode"](~/docs/ide/media/extensionmethod.gif "ExtensionMethod")|Erweiterungsmethode|![Symbol "Deklaration"](~/docs/ide/media/vxmethod_icon.gif "vxMethod\_Icon")|Externe Deklaration|  
|![Symbol "Delegat"](~/docs/ide/media/vxdelegate_icon.gif "vxDelegate\_Icon")|Delegat|![Fehlersymbol für Klassenansicht und Objektkatalog](~/docs/ide/media/erroricon.gif "ErrorIcon")|Fehler|  
|![Symbol "Ausnahme"](~/docs/ide/media/vxexception_icon.gif "vxException\_Icon")|Ausnahme|![Symbol "Vorlage"](~/docs/ide/media/vxtemplate_icon.gif "vxTemplate\_Icon")|Vorlage|  
|![Symbol "Zuordnung"](~/docs/ide/media/vxmap_icon.gif "vxMap\_Icon")|Zuordnung|![Symbol "Fehler &#45; Ausrufezeichen"](~/docs/ide/media/vxerror_icon.gif "vxError\_Icon")|Unbekannt|  
|![Symbol "Typweiterleitung"](~/docs/ide/media/ob_type_forward.gif "ob\_type\_forward")|Typweiterleitung|||  
  
## Signalsymbole  
 Die folgenden Signalsymbole gelten für alle vorgenannten Symbole und zeigen die Möglichkeit zum Zugriff auf diese an.  
  
> [!NOTE]
>  Wenn das Projekt in einer Quellcodeverwaltungs\-Datenbank enthalten ist, können zusätzliche Signalsymbole angezeigt werden, die den Quellcodeverwaltungsstatus angeben, beispielsweise eingecheckt oder ausgecheckt.  
  
|Symbol|Beschreibung|  
|------------|------------------|  
|\<Kein Signalsymbol\>|Public.  Der Zugriff ist von jeder Position innerhalb dieser Komponente und von jeder Komponente, die darauf verweist, möglich.|  
|![Symbol "Signal geschützt"](~/docs/ide/media/vxsignal_icon_key.gif "vxSignal\_Icon\_Key")|Protected.  Der Zugriff ist von der enthaltenden Klasse oder dem enthaltenden Typ oder von abgeleiteten Klassen oder Typen möglich.|  
|![Symbol "Signal privat"](~/docs/ide/media/vxsignal_icon_lock.gif "vxSignal\_Icon\_Lock")|Private.  Der Zugriff ist nur innerhalb der enthaltenden Klasse oder des enthaltenden Typs möglich.|  
|![Symbol "Signal versiegelt"](~/docs/ide/media/vxsignal_icon_envelope.gif "vxSignal\_Icon\_Envelope")|Versiegelt.|  
|![Symbol "Signal Friend&#47;Intern"](~/docs/ide/media/vxsignal_icon_diamond.gif "vxSignal\_Icon\_Diamond")|Freund\/intern.  Der Zugriff ist nur über das Projekt möglich.|  
|![Signalsymbol "Pfeil"](~/docs/ide/media/vxsignal_icon_arrow.gif "vxSignal\_Icon\_Arrow")|Shortcut.  Eine Verknüpfung zum Objekt.|  
  
## Siehe auch  
 [Anzeigen der Codestruktur](../ide/viewing-the-structure-of-code.md)
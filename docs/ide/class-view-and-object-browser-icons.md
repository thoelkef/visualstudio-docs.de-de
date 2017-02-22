---
title: "Symbole in der Klassenansicht und im Objektbrowser | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
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
caps.handback.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Symbole in der Klassenansicht und im Objektbrowser
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die **Klassenansicht** und der **Objektkatalog** enthalten eine Reihe von Symbolen, die Codeentitäten darstellen, z. B. Namespaces, Klassen, Funktionen oder Variablen.  In der folgenden Tabelle werden die Symbole verdeutlicht und beschrieben.  
  
|Symbol|Beschreibung|Symbol|Beschreibung|  
|------------|------------------|------------|------------------|  
|![Symbol "Namespace"](../ide/media/vxnamespace_icon.png "vxNamespace\_Icon")|Namespace|![Symbol "Deklaration"](../ide/media/vxmethod_icon.png "vxMethod\_Icon")|Methode oder Funktion|  
|![Symbol "Klasse"](../ide/media/vxclass_icon.png "vxClass\_Icon")|Klasse|![Symbol "Operator"](../ide/media/vxoperator_icon.png "vxOperator\_Icon")|Operator|  
|![Schnittstellensymbol "Lollipop"](../ide/media/vxinterface_icon.png "vxInterface\_Icon")|Schnittstelle|![Symbol "Eigenschaften"](../ide/media/vxproperty_icon.png "vxProperty\_Icon")|Eigenschaft|  
|![Symbol "Struktur"](../ide/media/vxstruct_icon.png "vxStruct\_Icon")|Struktur|![Symbol "Feld"](../ide/media/vxfield_icon.png "vxField\_Icon")|Feld oder Variable|  
|![Symbol "Union"](../ide/media/vxunion_icon.png "vxUnion\_Icon")|Union|![Symbol "Ereignis"](../ide/media/vxevent_icon.png "vxEvent\_Icon")|Ereignis|  
|![Symbol "Enumeration"](../ide/media/vxenum_icon.png "vxEnum\_Icon")|Enum|![Symbol "Konstante"](../ide/media/vxconstant_icon.png "vxConstant\_Icon")|Konstante|  
|![Symbol "Typdefinition"](../ide/media/vxtypedef_icon.png "vxTypeDef\_Icon")|TypeDef|![Symbol "Element enumerieren"](../ide/media/vxenumitem_icon.png "vxEnumItem\_Icon")|Enumerationselement|  
|![Symbol "Visual Studio&#45;Modul"](../ide/media/vxmodule_icon.png "vxModule\_Icon")|Modul|![Symbol "Zuordnungselement"](../ide/media/vxmapitem_icon.png "vxMapItem\_Icon")|Zuordnungselement|  
|![Symbol "Erweiterungsmethode"](../ide/media/extensionmethod.png "ExtensionMethod")|Erweiterungsmethode|![Symbol "Deklaration"](../ide/media/vxmethod_icon.png "vxMethod\_Icon")|Externe Deklaration|  
|![Symbol "Delegat"](../ide/media/vxdelegate_icon.png "vxDelegate\_Icon")|Delegat|![Fehlersymbol für Klassenansicht und Objektkatalog](../ide/media/erroricon.png "ErrorIcon")|Fehler|  
|![Symbol "Ausnahme"](../ide/media/vxexception_icon.png "vxException\_Icon")|Ausnahme|![Symbol "Vorlage"](../ide/media/vxtemplate_icon.png "vxTemplate\_Icon")|Vorlage|  
|![Symbol "Zuordnung"](../ide/media/vxmap_icon.png "vxMap\_Icon")|Zuordnung|![Symbol "Fehler &#45; Ausrufezeichen"](../ide/media/vxerror_icon.png "vxError\_Icon")|Unbekannt|  
|![Symbol "Typweiterleitung"](../ide/media/ob_type_forward.png "ob\_type\_forward")|Typweiterleitung|||  
  
## Signalsymbole  
 Die folgenden Signalsymbole gelten für alle vorgenannten Symbole und zeigen die Möglichkeit zum Zugriff auf diese an.  
  
> [!NOTE]
>  Wenn das Projekt in einer Quellcodeverwaltungs\-Datenbank enthalten ist, können zusätzliche Signalsymbole angezeigt werden, die den Quellcodeverwaltungsstatus angeben, beispielsweise eingecheckt oder ausgecheckt.  
  
|Symbol|Beschreibung|  
|------------|------------------|  
|\<Kein Signalsymbol\>|Public.  Der Zugriff ist von jeder Position innerhalb dieser Komponente und von jeder Komponente, die darauf verweist, möglich.|  
|![Symbol "Signal geschützt"](../ide/media/vxsignal_icon_key.png "vxSignal\_Icon\_Key")|Protected.  Der Zugriff ist von der enthaltenden Klasse oder dem enthaltenden Typ oder von abgeleiteten Klassen oder Typen möglich.|  
|![Symbol "Signal privat"](../ide/media/vxsignal_icon_lock.png "vxSignal\_Icon\_Lock")|Private.  Der Zugriff ist nur innerhalb der enthaltenden Klasse oder des enthaltenden Typs möglich.|  
|![Symbol "Signal versiegelt"](../ide/media/vxsignal_icon_envelope.png "vxSignal\_Icon\_Envelope")|Versiegelt.|  
|![Symbol "Signal Friend&#47;Intern"](../ide/media/vxsignal_icon_diamond.png "vxSignal\_Icon\_Diamond")|Freund\/intern.  Der Zugriff ist nur über das Projekt möglich.|  
|![Signalsymbol "Pfeil"](../ide/media/vxsignal_icon_arrow.png "vxSignal\_Icon\_Arrow")|Shortcut.  Eine Verknüpfung zum Objekt.|  
  
## Siehe auch  
 [Anzeigen der Codestruktur](../ide/viewing-the-structure-of-code.md)
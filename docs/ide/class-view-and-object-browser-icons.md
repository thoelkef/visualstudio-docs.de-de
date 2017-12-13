---
title: Symbole in der Klassenansicht und im Objektkatalog | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- icons, in Object Browser
- signal icons
- Class View tool, symbols
- graphic symbols
- IntelliSense, icons
- icons, IntelliSense
- symbols, Object Browser icons
- Object Browser, icons in Class View
ms.assetid: 58cc3f44-c296-4a88-a008-09d28598d9c0
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6b6fad74a71e457759bc6b35ecb4679c3f26011e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="class-view-and-object-browser-icons"></a>Symbole in der Klassenansicht und im Objektbrowser
Die **Klassenansicht** und der **Objektkatalog** zeigen Symbole an, die Codeentitäten darstellen, z.B. Namespaces, Klassen, Funktionen und Variablen. In der folgenden Tabelle werden die Symbole dargestellt und beschrieben.  
  
|Symbol|Beschreibung|Symbol|Beschreibung|  
|----------|-----------------|----------|-----------------|  
|![Symbol „Namespace“](../ide/media/vxnamespace_icon.gif "vxNamespace_Icon")|Namespace|![Symbol „Deklaration“](../ide/media/vxmethod_icon.gif "vxMethod_Icon")|Methode oder Funktion|  
|![Symbol „Klasse“](../ide/media/vxclass_icon.gif "vxClass_Icon")|Klasse|![Symbol „Operator“](../ide/media/vxoperator_icon.gif "vxOperator_Icon")|Operator|  
|![Symbol „Lollipopschnittstelle“](../ide/media/vxinterface_icon.gif "vxInterface_Icon")|Schnittstelle|![Symbol „Eigenschaften“](../ide/media/vxproperty_icon.gif "vxProperty_Icon")|Eigenschaft|  
|![Symbol „Struktur“](../ide/media/vxstruct_icon.gif "vxStruct_Icon")|Struktur|![Symbol „Feld“](../ide/media/vxfield_icon.gif "vxField_Icon")|Feld oder Variable|  
|![Symbol „Union“](../ide/media/vxunion_icon.gif "vxUnion_Icon")|Union|![Symbol „Ereignis“](../ide/media/vxevent_icon.gif "vxEvent_Icon")|Ereignis|  
|![Symbol „Enumeration“](../ide/media/vxenum_icon.gif "vxEnum_Icon")|Enum|![Symbol „Konstante“](../ide/media/vxconstant_icon.gif "vxConstant_Icon")|Konstante|  
|![Symbol „Typdefinition“](../ide/media/vxtypedef_icon.gif "vxTypeDef_Icon")|TypeDef|![Symbol „Element auflisten“](../ide/media/vxenumitem_icon.gif "vxEnumItem_Icon")|Enum-Element|  
|![Symbol „Visual Studio-Modul“](../ide/media/vxmodule_icon.gif "vxModule_Icon")|Modul|![Symbol „Zuordnungselement“](../ide/media/vxmapitem_icon.gif "vxMapItem_Icon")|Zuordnungselement|  
|![Symbol „Erweiterungsmethode“](../ide/media/extensionmethod.gif "ExtensionMethod")|Erweiterungsmethode|![Symbol „Deklaration“](../ide/media/vxmethod_icon.gif "vxMethod_Icon")|Externe Deklaration|  
|![Symbol „Delegat“](../ide/media/vxdelegate_icon.gif "vxDelegate_Icon")|Delegate|![Fehlersymbol für Klassenansicht und Objektkatalog](../ide/media/erroricon.gif "ErrorIcon")|Fehler|  
|![Symbol „Ausnahme“](../ide/media/vxexception_icon.gif "vxException_Icon")|Ausnahme|![Symbol „Vorlage“](../ide/media/vxtemplate_icon.gif "vxTemplate_Icon")|Vorlage|  
|![Symbol „Zuordnung“](../ide/media/vxmap_icon.gif "vxMap_Icon")|Zuordnung|![Symbol „Fehler – Ausrufezeichen“](../ide/media/vxerror_icon.gif "vxError_Icon")|Unbekannt|  
|![Symbol „Typweiterleitung“](../ide/media/ob_type_forward.gif "ob_type_forward")|Typweiterleitung|||  
  
## <a name="signal-icons"></a>Signalsymbole  
 Die folgenden Signalsymbole gelten für alle zuvor erwähnten Symbole und geben deren Barrierefreiheit an.  
  
> [!NOTE]
>  Wenn Ihr Projekt in einer Quellcodeverwaltungs-Datenbank enthalten ist, werden möglicherweise zusätzliche Signalsymbole angezeigt, um den Quellcodestatus anzugeben, z.B. eingecheckt oder ausgecheckt.  
  
|Symbol|Beschreibung|  
|----------|-----------------|  
|\<Kein Signalsymbol>|Öffentlich. Der komponenteninterne Zugriff ist möglich. Außerdem können andere Komponenten, die auf die Komponente verweisen, auf diese zugreifen.|  
|![Signalsymbol „Geschützt“](../ide/media/vxsignal_icon_key.gif "vxSignal_Icon_Key")|Geschützt. Der Zugriff ist innerhalb der enthaltenen Klasse oder dem enthaltenen Typ möglich. Außerdem haben Klassen oder Typen Zugriff, die von der enthaltenen Klasse oder dem enthaltenen Typ abgeleitet sind.|  
|![Signalsymbol „Privat“](../ide/media/vxsignal_icon_lock.gif "vxSignal_Icon_Lock")|Privat. Der Zugriff ist nur in der enthaltenden Klasse oder dem Typ möglich.|  
|![Signalsymbol „Versiegelt“](../ide/media/vxsignal_icon_envelope.gif "vxSignal_Icon_Envelope")|Versiegelt.|  
|![Signalsymbol „Friend/Intern“](../ide/media/vxsignal_icon_diamond.gif "vxSignal_Icon_Diamond")|Friend/Intern. Der Zugriff ist nur über das Projekt möglich.|  
|![Signalsymbol „Pfeil“](../ide/media/vxsignal_icon_arrow.gif "vxSignal_Icon_Arrow")|Verknüpfung. Eine Verknüpfung mit dem Objekt.|  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen der Codestruktur](../ide/viewing-the-structure-of-code.md)
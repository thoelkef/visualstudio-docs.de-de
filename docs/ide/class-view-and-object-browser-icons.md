---
title: Symbole in der Klassenansicht und im Objektbrowser
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- icons, in Object Browser
- signal icons
- Class View tool, symbols
- graphic symbols
- IntelliSense, icons
- icons, IntelliSense
- symbols, Object Browser icons
- Object Browser, icons in Class View
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 44b86f079feceebf00bb1a39adcf3ab84622474d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="class-view-and-object-browser-icons"></a>Symbole in der Klassenansicht und im Objektkatalog

Die **Klassenansicht** und der **Objektkatalog** zeigen Symbole an, die Codeentitäten darstellen, z.B. Namespaces, Klassen, Funktionen und Variablen. In der folgenden Tabelle werden die Symbole dargestellt und beschrieben.

|Symbol|description|Symbol|description|
|----------|-----------------|----------|-----------------|
|![Symbol „Namespace“](../ide/media/vxnamespace_icon.gif "vxNamespace_Icon")|Namespace|![Symbol „Deklaration“](../ide/media/vxmethod_icon.gif "vxMethod_Icon")|Methode oder Funktion|
|![Symbol „Klasse“](../ide/media/vxclass_icon.gif "vxClass_Icon")|Klasse|![Symbol „Operator“](../ide/media/vxoperator_icon.gif "vxOperator_Icon")|Operator|
|![Symbol „Lollipopschnittstelle“](../ide/media/vxinterface_icon.gif "vxInterface_Icon")|Interface|![Symbol „Eigenschaften“](../ide/media/vxproperty_icon.gif "vxProperty_Icon")|Eigenschaft|
|![Symbol „Struktur“](../ide/media/vxstruct_icon.gif "vxStruct_Icon")|Struktur|![Symbol „Feld“](../ide/media/vxfield_icon.gif "vxField_Icon")|Feld oder Variable|
|![Symbol „Union“](../ide/media/vxunion_icon.gif "vxUnion_Icon")|Union|![Symbol „Ereignis“](../ide/media/vxevent_icon.gif "vxEvent_Icon")|event|
|![Symbol „Enumeration“](../ide/media/vxenum_icon.gif "vxEnum_Icon")|Enum|![Symbol „Konstante“](../ide/media/vxconstant_icon.gif "vxConstant_Icon")|Konstante|
|![Symbol „Typdefinition“](../ide/media/vxtypedef_icon.gif "vxTypeDef_Icon")|TypeDef|![Symbol „Element auflisten“](../ide/media/vxenumitem_icon.gif "vxEnumItem_Icon")|Enum-Element|
|![Symbol „Visual Studio-Modul“](../ide/media/vxmodule_icon.gif "vxModule_Icon")|Modul|![Symbol „Zuordnungselement“](../ide/media/vxmapitem_icon.gif "vxMapItem_Icon")|Zuordnungselement|
|![Symbol „Erweiterungsmethode“](../ide/media/extensionmethod.gif "ExtensionMethod")|Erweiterungsmethode|![Symbol „Deklaration“](../ide/media/vxmethod_icon.gif "vxMethod_Icon")|Externe Deklaration|
|![Symbol „Delegat“](../ide/media/vxdelegate_icon.gif "vxDelegate_Icon")|delegate|![Fehlersymbol für Klassenansicht und Objektkatalog](../ide/media/erroricon.gif "ErrorIcon")|Fehler|
|![Symbol „Ausnahme“](../ide/media/vxexception_icon.gif "vxException_Icon")|Ausnahme|![Symbol „Vorlage“](../ide/media/vxtemplate_icon.gif "vxTemplate_Icon")|Vorlage|
|![Symbol „Zuordnung“](../ide/media/vxmap_icon.gif "vxMap_Icon")|Zuordnung|![Symbol „Fehler – Ausrufezeichen“](../ide/media/vxerror_icon.gif "vxError_Icon")|Unbekannt|
|![Symbol „Typweiterleitung“](../ide/media/ob_type_forward.gif "ob_type_forward")|Typweiterleitung|||

## <a name="signal-icons"></a>Signalsymbole

Die folgenden Signalsymbole gelten für alle zuvor erwähnten Symbole und geben deren Barrierefreiheit an.

|Symbol|description|
|----------|-----------------|
|\<Kein Signalsymbol>|Öffentlich. Der komponenteninterne Zugriff ist möglich. Außerdem können andere Komponenten, die auf die Komponente verweisen, auf diese zugreifen.|
|![Signalsymbol „Geschützt“](../ide/media/vxsignal_icon_key.gif "vxSignal_Icon_Key")|Geschützt. Der Zugriff ist innerhalb der enthaltenen Klasse oder dem enthaltenen Typ möglich. Außerdem haben Klassen oder Typen Zugriff, die von der enthaltenen Klasse oder dem enthaltenen Typ abgeleitet sind.|
|![Signalsymbol „Privat“](../ide/media/vxsignal_icon_lock.gif "vxSignal_Icon_Lock")|Privat. Der Zugriff ist nur in der enthaltenden Klasse oder dem Typ möglich.|
|![Signalsymbol „Versiegelt“](../ide/media/vxsignal_icon_envelope.gif "vxSignal_Icon_Envelope")|Versiegelt.|
|![Signalsymbol „Friend/Intern“](../ide/media/vxsignal_icon_diamond.gif "vxSignal_Icon_Diamond")|Friend/Intern. Der Zugriff ist nur über das Projekt möglich.|
|![Signalsymbol „Pfeil“](../ide/media/vxsignal_icon_arrow.gif "vxSignal_Icon_Arrow")|Verknüpfung. Eine Verknüpfung mit dem Objekt.|

> [!NOTE]
> Wenn Ihr Projekt in einer Quellcodeverwaltungs-Datenbank enthalten ist, werden möglicherweise zusätzliche Signalsymbole angezeigt, um den Quellcodestatus anzugeben, z.B. eingecheckt oder ausgecheckt.

## <a name="see-also"></a>Siehe auch

- [Anzeigen der Codestruktur](../ide/viewing-the-structure-of-code.md)
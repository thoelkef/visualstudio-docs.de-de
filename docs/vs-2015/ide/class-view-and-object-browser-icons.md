---
title: Symbole in der Klassenansicht und im Objektkatalog | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3e67763234ff7b3778cccabaed45fbbc0bc04d30
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72620486"
---
# <a name="class-view-and-object-browser-icons"></a>Symbole in der Klassenansicht und im Objektbrowser
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Klassenansicht * * und das **Objektkatalog** Symbole anzeigen, die Code Entitäten darstellen, z. b. Namespaces, Klassen, Funktionen und Variablen. In der folgenden Tabelle werden die Symbole dargestellt und beschrieben.

|Symbol|Beschreibung|Symbol|Beschreibung|
|----------|-----------------|----------|-----------------|
|![Symbol "Namespace"](../ide/media/vxnamespace-icon.gif "vxNamespace_Icon")|Namespace|![Symbol "Deklaration"](../ide/media/vxmethod-icon.gif "vxMethod_Icon")|Methode oder Funktion|
|![Symbol "Klasse"](../ide/media/vxclass-icon.gif "vxClass_Icon")|Klasse|![Symbol "Operator"](../ide/media/vxoperator-icon.gif "vxOperator_Icon")|Operator|
|![Schnittstellensymbol "Lollipop"](../ide/media/vxinterface-icon.gif "vxInterface_Icon")|Interface|![Symbol "Eigenschaften"](../ide/media/vxproperty-icon.gif "vxProperty_Icon")|Eigenschaft|
|![Symbol "Struktur"](../ide/media/vxstruct-icon.gif "vxStruct_Icon")|Struktur|![Symbol "Feld"](../ide/media/vxfield-icon.gif "vxField_Icon")|Feld oder Variable|
|![Symbol "Union"](../ide/media/vxunion-icon.gif "vxUnion_Icon")|Union|![Symbol "Ereignis"](../ide/media/vxevent-icon.gif "vxEvent_Icon")|event|
|![Symbol "Enumeration"](../ide/media/vxenum-icon.gif "vxEnum_Icon")|Enum|![Symbol "Konstante"](../ide/media/vxconstant-icon.gif "vxConstant_Icon")|Konstante|
|![Symbol "Typdefinition"](../ide/media/vxtypedef-icon.gif "vxTypeDef_Icon")|TypeDef|![Symbol "Element enumerieren"](../ide/media/vxenumitem-icon.gif "vxEnumItem_Icon")|Enum-Element|
|![Symbol "Visual Studio-Modul"](../ide/media/vxmodule-icon.gif "vxModule_Icon")|Modul|![Symbol "Zuordnungselement"](../ide/media/vxmapitem-icon.gif "vxMapItem_Icon")|Zuordnungselement|
|![Symbol "Erweiterungsmethode"](../ide/media/extensionmethod.gif "Extensionmethod")|Erweiterungsmethode|![Symbol "Deklaration"](../ide/media/vxmethod-icon.gif "vxMethod_Icon")|Externe Deklaration|
|![Symbol "Delegat"](../ide/media/vxdelegate-icon.gif "vxDelegate_Icon")|delegate|![Fehlersymbol für Klassenansicht und Objektkatalog](../ide/media/erroricon.gif "Erroricon")|Fehler|
|![Symbol "Ausnahme"](../ide/media/vxexception-icon.gif "vxException_Icon")|Ausnahme|![Symbol "Vorlage"](../ide/media/vxtemplate-icon.gif "vxTemplate_Icon")|Vorlage|
|![Symbol "Zuordnung"](../ide/media/vxmap-icon.gif "vxMap_Icon")|Zuordnung|![Symbol "Fehler - Ausrufezeichen"](../ide/media/vxerror-icon.gif "vxError_Icon")|Unbekannt|
|![Symbol "Typweiterleitung"](../ide/media/ob-type-forward.gif "ob_type_forward")|Typweiterleitung|||

## <a name="signal-icons"></a>Signalsymbole
 Die folgenden Signalsymbole gelten für alle zuvor erwähnten Symbole und geben deren Barrierefreiheit an.

> [!NOTE]
> Wenn Ihr Projekt in einer Quellcodeverwaltungs-Datenbank enthalten ist, werden möglicherweise zusätzliche Signalsymbole angezeigt, um den Quellcodestatus anzugeben, z.B. eingecheckt oder ausgecheckt.

|Symbol|Beschreibung|
|----------|-----------------|
|\<No Signal Icon>|Öffentlich. Der komponenteninterne Zugriff ist möglich. Außerdem können andere Komponenten, die auf die Komponente verweisen, auf diese zugreifen.|
|![Symbol "Signal geschützt"](../ide/media/vxsignal-icon-key.gif "vxSignal_Icon_Key")|Geschützt. Der Zugriff ist innerhalb der enthaltenen Klasse oder dem enthaltenen Typ möglich. Außerdem haben Klassen oder Typen Zugriff, die von der enthaltenen Klasse oder dem enthaltenen Typ abgeleitet sind.|
|![Symbol "Signal privat"](../ide/media/vxsignal-icon-lock.gif "vxSignal_Icon_Lock")|Privat. Der Zugriff ist nur in der enthaltenden Klasse oder dem Typ möglich.|
|![Symbol "Signal versiegelt"](../ide/media/vxsignal-icon-envelope.gif "vxSignal_Icon_Envelope")|Versiegelt.|
|![Signal Friend&#47;internes Symbol](../ide/media/vxsignal-icon-diamond.gif "vxSignal_Icon_Diamond")|Friend/Intern. Der Zugriff ist nur über das Projekt möglich.|
|![Signalsymbol "Pfeil"](../ide/media/vxsignal-icon-arrow.gif "vxSignal_Icon_Arrow")|Verknüpfung. Eine Verknüpfung mit dem Objekt.|

## <a name="see-also"></a>Weitere Informationen
 [Anzeigen der Code Struktur](../ide/viewing-the-structure-of-code.md)

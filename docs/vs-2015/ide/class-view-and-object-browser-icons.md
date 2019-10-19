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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72620486"
---
# <a name="class-view-and-object-browser-icons"></a>Symbole in der Klassenansicht und im Objektbrowser
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die **Klassenansicht** und der **Objektkatalog** zeigen Symbole an, die Codeentitäten darstellen, z.B. Namespaces, Klassen, Funktionen und Variablen. In der folgenden Tabelle werden die Symbole dargestellt und beschrieben.

|Symbol|Beschreibung|Symbol|Beschreibung|
|----------|-----------------|----------|-----------------|
|![Namespace Symbol](../ide/media/vxnamespace-icon.gif "vxNamespace_Icon")|Namespace|![Deklarations Symbol](../ide/media/vxmethod-icon.gif "vxMethod_Icon")|Methode oder Funktion|
|![Klassen Symbol](../ide/media/vxclass-icon.gif "vxClass_Icon")|Klasse|![Operator Symbol](../ide/media/vxoperator-icon.gif "vxOperator_Icon")|Operator|
|![Lollipop-Schnittstellen Symbol](../ide/media/vxinterface-icon.gif "vxInterface_Icon")|Interface|![Eigenschafts Symbol](../ide/media/vxproperty-icon.gif "vxProperty_Icon")|property|
|![Struktur Symbol](../ide/media/vxstruct-icon.gif "vxStruct_Icon")|Struktur|![Symbol "Feld"](../ide/media/vxfield-icon.gif "vxField_Icon")|Feld oder Variable|
|![Union-Symbol](../ide/media/vxunion-icon.gif "vxUnion_Icon")|Union|![Ereignis Symbol](../ide/media/vxevent-icon.gif "vxEvent_Icon")|event|
|![Enumerationssymbol](../ide/media/vxenum-icon.gif "vxEnum_Icon")|Enum|![Konstantes Symbol](../ide/media/vxconstant-icon.gif "vxConstant_Icon")|Konstante|
|![Typdefinitions Symbol](../ide/media/vxtypedef-icon.gif "vxTypeDef_Icon")|TypeDef|![Element Symbol aufzählen](../ide/media/vxenumitem-icon.gif "vxEnumItem_Icon")|Enum-Element|
|![Visual Studio-Modul Symbol](../ide/media/vxmodule-icon.gif "vxModule_Icon")|Modul|![Symbol "Kartenelement"](../ide/media/vxmapitem-icon.gif "vxMapItem_Icon")|Zuordnungselement|
|![Symbol "Erweiterungsmethode"](../ide/media/extensionmethod.gif "Extensionmethod")|Erweiterungsmethode|![Deklarations Symbol](../ide/media/vxmethod-icon.gif "vxMethod_Icon")|Externe Deklaration|
|![Delegatsymbol](../ide/media/vxdelegate-icon.gif "vxDelegate_Icon")|delegate|![Fehler Symbol für Klassenansicht und Objektkatalog](../ide/media/erroricon.gif "Erroricon")|Fehler|
|![Ausnahme Symbol](../ide/media/vxexception-icon.gif "vxException_Icon")|-Ausnahme|![Vorlagen Symbol](../ide/media/vxtemplate-icon.gif "vxTemplate_Icon")|Vorlage|
|![Karten Symbol](../ide/media/vxmap-icon.gif "vxMap_Icon")|Zuordnung|![Fehler Ausrufezeichen-Symbol](../ide/media/vxerror-icon.gif "vxError_Icon")|Unbekannt|
|![Symbol für Typweiterleitung](../ide/media/ob-type-forward.gif "ob_type_forward")|Typweiterleitung|||

## <a name="signal-icons"></a>Signalsymbole
 Die folgenden Signalsymbole gelten für alle zuvor erwähnten Symbole und geben deren Barrierefreiheit an.

> [!NOTE]
> Wenn Ihr Projekt in einer Quellcodeverwaltungs-Datenbank enthalten ist, werden möglicherweise zusätzliche Signalsymbole angezeigt, um den Quellcodestatus anzugeben, z.B. eingecheckt oder ausgecheckt.

|Symbol|Beschreibung|
|----------|-----------------|
|\<Kein Signalsymbol>|Öffentlich. Der komponenteninterne Zugriff ist möglich. Außerdem können andere Komponenten, die auf die Komponente verweisen, auf diese zugreifen.|
|![Signal geschütztes Symbol](../ide/media/vxsignal-icon-key.gif "vxSignal_Icon_Key")|Geschützt. Der Zugriff ist innerhalb der enthaltenen Klasse oder dem enthaltenen Typ möglich. Außerdem haben Klassen oder Typen Zugriff, die von der enthaltenen Klasse oder dem enthaltenen Typ abgeleitet sind.|
|![Symbol "privates Signal"](../ide/media/vxsignal-icon-lock.gif "vxSignal_Icon_Lock")|Privat. Der Zugriff ist nur in der enthaltenden Klasse oder dem Typ möglich.|
|![Signal versiegeltes Symbol](../ide/media/vxsignal-icon-envelope.gif "vxSignal_Icon_Envelope")|Versiegelt.|
|![Internes Signal&#47;Friend-Symbol](../ide/media/vxsignal-icon-diamond.gif "vxSignal_Icon_Diamond")|Friend/Intern. Der Zugriff ist nur über das Projekt möglich.|
|![Signal Symbol Pfeil](../ide/media/vxsignal-icon-arrow.gif "vxSignal_Icon_Arrow")|Verknüpfung. Eine Verknüpfung mit dem Objekt.|

## <a name="see-also"></a>Siehe auch
 [Anzeigen der Codestruktur](../ide/viewing-the-structure-of-code.md)

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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7cb80c7ad81708724750660560d65cfef722af86
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54785048"
---
# <a name="class-view-and-object-browser-icons"></a>Symbole in der Klassenansicht und im Objektbrowser
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die **Klassenansicht** und der **Objektkatalog** zeigen Symbole an, die Codeentitäten darstellen, z.B. Namespaces, Klassen, Funktionen und Variablen. In der folgenden Tabelle werden die Symbole dargestellt und beschrieben.  
  
|Symbol|Beschreibung|Symbol|Beschreibung|  
|----------|-----------------|----------|-----------------|  
|![Symbol „Namespace“](../ide/media/vxnamespace-icon.gif "vxNamespace_Icon")|Namespace|![Symbol „Deklaration“](../ide/media/vxmethod-icon.gif "vxMethod_Icon")|Methode oder Funktion|  
|![Symbol „Klasse“](../ide/media/vxclass-icon.gif "vxClass_Icon")|Klasse|![Symbol „Operator“](../ide/media/vxoperator-icon.gif "vxOperator_Icon")|Operator|  
|![Symbol „Lollipopschnittstelle“](../ide/media/vxinterface-icon.gif "vxInterface_Icon")|Interface|![Symbol „Eigenschaften“](../ide/media/vxproperty-icon.gif "vxProperty_Icon")|Eigenschaft|  
|![Symbol „Struktur“](../ide/media/vxstruct-icon.gif "vxStruct_Icon")|Struktur|![Symbol „Feld“](../ide/media/vxfield-icon.gif "vxField_Icon")|Feld oder Variable|  
|![Symbol „Union“](../ide/media/vxunion-icon.gif "vxUnion_Icon")|Union|![Symbol „Ereignis“](../ide/media/vxevent-icon.gif "vxEvent_Icon")|event|  
|![Symbol „Enumeration“](../ide/media/vxenum-icon.gif "vxEnum_Icon")|Enum|![Symbol „Konstante“](../ide/media/vxconstant-icon.gif "vxConstant_Icon")|Konstante|  
|![Symbol „Typdefinition“](../ide/media/vxtypedef-icon.gif "vxTypeDef_Icon")|TypeDef|![Symbol „Element auflisten“](../ide/media/vxenumitem-icon.gif "vxEnumItem_Icon")|Enum-Element|  
|![Symbol „Visual Studio-Modul“](../ide/media/vxmodule-icon.gif "vxModule_Icon")|Modul|![Symbol „Zuordnungselement“](../ide/media/vxmapitem-icon.gif "vxMapItem_Icon")|Zuordnungselement|  
|![Symbol „Erweiterungsmethode“](../ide/media/extensionmethod.gif "ExtensionMethod")|Erweiterungsmethode|![Symbol „Deklaration“](../ide/media/vxmethod-icon.gif "vxMethod_Icon")|Externe Deklaration|  
|![Symbol „Delegat“](../ide/media/vxdelegate-icon.gif "vxDelegate_Icon")|delegate|![Fehlersymbol für Klassenansicht und Objektkatalog](../ide/media/erroricon.gif "ErrorIcon")|Fehler|  
|![Symbol „Ausnahme“](../ide/media/vxexception-icon.gif "vxException_Icon")|Ausnahme|![Symbol „Vorlage“](../ide/media/vxtemplate-icon.gif "vxTemplate_Icon")|Vorlage|  
|![Symbol „Zuordnung“](../ide/media/vxmap-icon.gif "vxMap_Icon")|Zuordnung|![Symbol „Fehler – Ausrufezeichen“](../ide/media/vxerror-icon.gif "vxError_Icon")|Unbekannt|  
|![Symbol „Typweiterleitung“](../ide/media/ob-type-forward.gif "ob_type_forward")|Typweiterleitung|||  
  
## <a name="signal-icons"></a>Signalsymbole  
 Die folgenden Signalsymbole gelten für alle zuvor erwähnten Symbole und geben deren Barrierefreiheit an.  
  
> [!NOTE]
>  Wenn Ihr Projekt in einer Quellcodeverwaltungs-Datenbank enthalten ist, werden möglicherweise zusätzliche Signalsymbole angezeigt, um den Quellcodestatus anzugeben, z.B. eingecheckt oder ausgecheckt.  
  
|Symbol|Beschreibung|  
|----------|-----------------|  
|\<Kein Signalsymbol>|Öffentlich. Der komponenteninterne Zugriff ist möglich. Außerdem können andere Komponenten, die auf die Komponente verweisen, auf diese zugreifen.|  
|![Signalsymbol „Geschützt“](../ide/media/vxsignal-icon-key.gif "vxSignal_Icon_Key")|Geschützt. Der Zugriff ist innerhalb der enthaltenen Klasse oder dem enthaltenen Typ möglich. Außerdem haben Klassen oder Typen Zugriff, die von der enthaltenen Klasse oder dem enthaltenen Typ abgeleitet sind.|  
|![Signalsymbol „Privat“](../ide/media/vxsignal-icon-lock.gif "vxSignal_Icon_Lock")|Privat. Der Zugriff ist nur in der enthaltenden Klasse oder dem Typ möglich.|  
|![Signalsymbol „Versiegelt“](../ide/media/vxsignal-icon-envelope.gif "vxSignal_Icon_Envelope")|Versiegelt.|  
|![Signalsymbol „Friend/Intern“](../ide/media/vxsignal-icon-diamond.gif "vxSignal_Icon_Diamond")|Friend/Intern. Der Zugriff ist nur über das Projekt möglich.|  
|![Signalsymbol „Pfeil“](../ide/media/vxsignal-icon-arrow.gif "vxSignal_Icon_Arrow")|Verknüpfung. Eine Verknüpfung mit dem Objekt.|  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen der Codestruktur](../ide/viewing-the-structure-of-code.md)

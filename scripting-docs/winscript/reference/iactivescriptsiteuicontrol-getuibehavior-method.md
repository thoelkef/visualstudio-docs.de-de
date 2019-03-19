---
title: 'Iactivescriptsiteuicontrol:: Getuibehavior-Methode | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 9a944335-856a-4c6b-b2bc-8872542941b7
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e3f6247afc70ef1197ea759ffdf475c2d6c0a0c
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58158213"
---
# <a name="iactivescriptsiteuicontrolgetuibehavior-method"></a>IActiveScriptSiteUIControl::GetUIBehavior-Methode
Ruft eine [SCRIPTUICHANDLING-Enumeration](../../winscript/reference/scriptuichandling-enumeration.md) , darstellt, wie ein UI-Steuerelement behandelt werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetUIBehavior(     [in] SCRIPTUICITEM UicItem,     [out] SCRIPTUICHANDLING * pUicHandling );   
```  
  
#### <a name="parameters"></a>Parameter  
 `UicItem`  
 Der Typ des Steuerelements.  
  
 `pUicHandling`  
 Die Möglichkeit, die das Steuerelement behandelt werden soll.
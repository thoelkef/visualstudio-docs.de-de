---
title: EVALFLAGS90 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- EVALFLAGS90 enumeration
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 120bf38afbf05f367757de3a5e453cab8b4311b1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="evalflags90"></a>EVALFLAGS90
Listet die gültigen Werte für die Flags, die Auswertung von Ausdrücken zu steuern. Diese Enumeration erweitert die [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) Enumeration.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_EVALFLAGS90  
{  
   // VS 8.0 values  
   EVAL90_RETURNVALUE                 = 0x0002,  
   EVAL90_NOSIDEEFFECTS               = 0x0004,  
   EVAL90_ALLOWBPS                    = 0x0008,  
   EVAL90_ALLOWERRORREPORT            = 0x0010,  
   EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,  
   EVAL90_NOFUNCEVAL                  = 0x0080,  
   EVAL90_NOEVENTS                    = 0x1000,  
   EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,  
   EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,  
  
   // Values added in VS 9.0  
   EVAL90_FORCE_EVALUATION_NOW        = 0x8000  
};  
typedef DWORD EVALFLAGS90;  
```  
  
```csharp  
public enum enum_EVALFLAGS90  
{  
   // VS 8.0 values  
   EVAL90_RETURNVALUE                 = 0x0002,  
   EVAL90_NOSIDEEFFECTS               = 0x0004,  
   EVAL90_ALLOWBPS                    = 0x0008,  
   EVAL90_ALLOWERRORREPORT            = 0x0010,  
   EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,  
   EVAL90_NOFUNCEVAL                  = 0x0080,  
   EVAL90_NOEVENTS                    = 0x1000,  
   EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,  
   EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,  
  
   // Values added in VS 9.0  
   EVAL90_FORCE_EVALUATION_NOW        = 0x8000  
};  
```  
  
#### <a name="parameters"></a>Parameter  
 EVAL90_RETURNVALUE  
 Gibt an, dass der Rückgabewert, sofern vorhanden, ausgewertet werden.  
  
 EVAL90_NOSIDEEFFECTS  
 Gibt an, dass Nebeneffekte nicht zulässig.  
  
 EVAL90_ALLOWBPS  
 Gibt den Beenden an Haltepunkten an.  
  
 EVAL90_ALLOWERRORREPORT  
 Gibt an, Fehlerberichte an den Host zugelassen werden. In erster Linie verwendet für die Auswertung von Ausdrücken im Skript in Internet Explorer.  
  
 EVAL90_FUNCTION_AS_ADDRESS  
 Erzwingt, dass Funktionen, die als Adressen, statt den Funktionsaufruf ausgewertet werden.  
  
 EVAL90_NOFUNCEVAL  
 Verhindern Sie, dass Funktion ausgewertet wird. Betrachten Sie beispielsweise die `int` token im Ausdruck `myExpression(int) + 10`. Diese Funktion kann als eine Adresse, jedoch nicht als Wert richtig ausgewertet werden.  
  
 EVAL90_NOEVENTS  
 Kennzeichen Sie, um anzugeben, dass Ereignisse während der Auswertung von Ausdrücken nicht zu der Sitzung Debug-Manager (SDM) oder der IDE gesendet werden sollen.  
  
 EVAL90_DESIGN_TIME_EXPR_EVAL  
 Ermöglicht die ausdrucksauswertung zur Entwurfszeit.  
  
 EVAL90_ALLOW_IMPLICIT_VARS  
 Ermöglicht implizite Variable erstellen.  
  
 EVAL90_FORCE_EVALUATION_NOW  
 Erzwingt die Auswertung sofort durchgeführt. Dies ist hilfreich, wenn eine Anforderung, z. B. eine benutzeranforderung Wartung.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Msdbg90.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
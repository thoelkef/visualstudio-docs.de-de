---
title: "FRAMEINFO_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FRAMEINFO_FLAGS"
helpviewer_keywords: 
  - "FRAMEINFO_FLAGS-enumeration"
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# FRAMEINFO_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt die Informationen an, die zu einem Stapelrahmen Objekt abzurufen.  
  
## Syntax  
  
```cpp#  
enum enum_FRAMEINFO_FLAGS {  
   FIF_FUNCNAME              = 0x00000001,  
   FIF_RETURNTYPE            = 0x00000002,  
   FIF_ARGS                  = 0x00000004,  
   FIF_LANGUAGE              = 0x00000008,  
   FIF_MODULE                = 0x00000010,  
   FIF_STACKRANGE            = 0x00000020,  
   FIF_FRAME                 = 0x00000040,  
   FIF_DEBUGINFO             = 0x00000080,  
   FIF_STALECODE             = 0x00000100,  
   FIF_ANNOTATEDFRAME        = 0x00000200,  
   FIF_DEBUG_MODULEP         = 0x00000400,  
   FIF_FUNCNAME_FORMAT       = 0x00001000,  
   FIF_FUNCNAME_RETURNTYPE   = 0x00002000,  
   FIF_FUNCNAME_ARGS         = 0x00004000,  
   FIF_FUNCNAME_LANGUAGE     = 0x00008000,  
   FIF_FUNCNAME_MODULE       = 0x00010000,  
   FIF_FUNCNAME_LINES        = 0x00020000,  
   FIF_FUNCNAME_OFFSET       = 0x00040000,  
   FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,  
   FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,  
   FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,  
   FIF_FUNCNAME_ARGS_ALL     = 0x00700000,  
   FIF_ARGS_TYPES            = 0x01000000,  
   FIF_ARGS_NAMES            = 0x02000000,  
   FIF_ARGS_VALUES           = 0x04000000,  
   FIF_ARGS_ALL              = 0x07000000,  
   FIF_ARGS_NOFORMAT         = 0x08000000,  
   FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,  
   FIF_FILTER_NON_USER_CODE  = 0x20000000,  
   FIF_ARGS_NO_TOSTRING      = 0x40000000,  
   FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000  
};  
typedef DWORD FRAMEINFO_FLAGS;  
```  
  
```c#  
public enum enum_FRAMEINFO_FLAGS {  
   FIF_FUNCNAME              = 0x00000001,  
   FIF_RETURNTYPE            = 0x00000002,  
   FIF_ARGS                  = 0x00000004,  
   FIF_LANGUAGE              = 0x00000008,  
   FIF_MODULE                = 0x00000010,  
   FIF_STACKRANGE            = 0x00000020,  
   FIF_FRAME                 = 0x00000040,  
   FIF_DEBUGINFO             = 0x00000080,  
   FIF_STALECODE             = 0x00000100,  
   FIF_ANNOTATEDFRAME        = 0x00000200,  
   FIF_DEBUG_MODULEP         = 0x00000400,  
   FIF_FUNCNAME_FORMAT       = 0x00001000,  
   FIF_FUNCNAME_RETURNTYPE   = 0x00002000,  
   FIF_FUNCNAME_ARGS         = 0x00004000,  
   FIF_FUNCNAME_LANGUAGE     = 0x00008000,  
   FIF_FUNCNAME_MODULE       = 0x00010000,  
   FIF_FUNCNAME_LINES        = 0x00020000,  
   FIF_FUNCNAME_OFFSET       = 0x00040000,  
   FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,  
   FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,  
   FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,  
   FIF_FUNCNAME_ARGS_ALL     = 0x00700000,  
   FIF_ARGS_TYPES            = 0x01000000,  
   FIF_ARGS_NAMES            = 0x02000000,  
   FIF_ARGS_VALUES           = 0x04000000,  
   FIF_ARGS_ALL              = 0x07000000,  
   FIF_ARGS_NOFORMAT         = 0x08000000,  
   FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,  
   FIF_FILTER_NON_USER_CODE  = 0x20000000,  
   FIF_ARGS_NO_TOSTRING      = 0x40000000,  
   FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000  
};  
```  
  
## Mitglieder  
 FIF\_FUNCNAME  
 Initialisieren Sie das Feld `m_bstrFuncName` \/verwenden.  
  
 FIF\_RETURNTYPE  
 Initialisieren Sie das Feld `m_bstrReturnType` \/verwenden.  
  
 FIF\_ARGS  
 Initialisieren Sie das Feld `m_bstrArgs` \/verwenden.  
  
 FIF\_LANGUAGE  
 Initialisieren Sie das Feld `m_bstrLanguage` \/verwenden.  
  
 FIF\_MODULE  
 Initialisieren Sie das Feld `m_bstrModule` \/verwenden.  
  
 FIF\_STACKRANGE  
 Initialisieren Sie die `m_addrMin` \/verwenden, und `m_addrMax` Bereich\), Felder \(Stapel.  
  
 FIF\_FRAME  
 Initialisieren Sie das Feld `m_pFrame` \/verwenden.  
  
 FIF\_DEBUGINFO  
 Initialisieren Sie das Feld `m_fHasDebugInfo` \/verwenden.  
  
 FIF\_STALECODE  
 Initialisieren Sie das Feld `m_fStaleCode` \/verwenden.  
  
 FIF\_ANNOTATEDFRAME  
 Initialisieren Sie das Feld `m_fAnnotatedFrame` \/verwenden.  
  
 FIF\_DEBUG\_MODULEP  
 Initialisieren Sie das Feld `m_pModule` \/verwenden.  
  
 FIF\_FUNCNAME\_FORMAT  
 Formatiert den Funktionsnamen.  Das Ergebnis wird im `m_bstrFunName` Feld zurückgegeben und keine anderen Felder werden geändert.  
  
 FIF\_FUNCNAME\_RETURNTYPE  
 Fügt den Rückgabetyp dem `m_bstrFuncName` Feld hinzu.  
  
 FIF\_FUNCNAME\_ARGS  
 Fügt den Argumenten der `m_bstrFuncName` Feld hinzu.  
  
 FIF\_FUNCNAME\_LANGUAGE  
 Fügt dem die Sprache `m_bstrFuncName` Feld hinzu.  
  
 FIF\_FUNCNAME\_MODULE  
 Fügt den Modulnamen dem `m_bstrFuncName` Feld hinzu.  
  
 FIF\_FUNCNAME\_LINES  
 Fügt dem die Anzahl der Zeilen `m_bstrFuncName` Feld hinzu.  
  
 FIF\_FUNCNAME\_OFFSET  
 Fügt dem `m_bstrFuncName` Feld den Offset in Bytes vom Anfang der Zeile hinzu, wenn `FIF_FUNCNAME_LINES` angegeben wird.  Wenn `FIF_FUNCNAME_LINES` nicht angegeben ist oder wenn die Zeilennummern nicht verfügbar sind, fügt den Offset in Bytes vom Anfang der Funktion hinzu.  
  
 FIF\_FUNCNAME\_ARGS\_TYPES  
 Fügt dem `m_bstrFuncName`\-Funktionsarguments den Typ jedes Felds.  
  
 FIF\_FUNCNAME\_ARGS\_NAMES  
 Fügt den Namen eines Funktionsarguments dem `m_bstrFuncName` Feld hinzu.  
  
 FIF\_FUNCNAME\_ARGS\_VALUES  
 Fügt dem `m_bstrFuncName`\-Funktionsarguments den Wert für jedes Feld hinzu.  
  
 FIF\_FUNCNAME\_ARGS\_ALL  
 Fügt den Typ, den Namen und den Wert aller Argumente dem `m_bstrFuncName` Feld hinzu.  
  
 FIF\_ARGS\_TYPES  
 Die Argumenttypen und abgerufen werden.  
  
 FIF\_ARGS\_NAMES  
 Die Argumentnamen und abgerufen werden.  
  
 FIF\_ARGS\_VALUES  
 Die Argumentwerte werden abgerufen und formatiert.  
  
 FIF\_ARGS\_ALL  
 Abrufen und formatieren Sie den Typ, den Namen und den Wert aller Argumente.  
  
 FIF\_ARGS\_NOFORMAT  
 Gibt an, dass die Argumente nicht formatiert werden sollen \(z. B. Add öffnenden und schließenden Klammer hinzu, um die Argumentliste nicht immer noch ein Trennzeichen zwischen Argumenten hinzu\).  
  
 FIF\_ARGS\_NO\_FUNC\_EVAL  
 Gibt diese Auswertung der Funktion \(Eigenschaft\) sollte nicht verwendet werden, wenn Argumentwerte abzurufen.  
  
 FIF\_FILTER\_NON\_USER\_CODE  
 Das Debugmodul ist, Nicht\-Benutzer Coderahmen zu filtern, daher werden sie nicht eingeschlossen.  
  
 FIF\_ARGS\_NO\_TOSTRING  
 Lassen Sie nicht `ToString()`\-Funktionsauswertung oder \- Formatierung, wenn Sie Funktionsargumente zurückgeben.  
  
 FIF\_DESIGN\_TIME\_EXPR\_EVAL  
 Feldinformationen sollten gehosteter APP DOMAIN statt der Hostprozess abgerufen werden.  
  
## Hinweise  
 Diese Flags werden auf die [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) und [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)\-Methode übergeben, um anzugeben, welche Felder in der [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Struktur oder \- Strukturen initialisiert werden sollen.  
  
 Diese Flags werden auch verwendet, um anzugeben, welche Felder der [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Struktur verwendet und gültig sind, wenn die Struktur zurückgegeben wird.  Diese Werte können mit bitweisen `OR`kombiniert werden.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
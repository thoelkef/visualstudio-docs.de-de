---
title: IDebugProgramNode2::GetHostName | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetHostName
helpviewer_keywords:
- IDebugProgramNode2::GetHostName
ms.assetid: 16aad1ff-ad34-4394-a2e4-5621374a7729
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c9f5768ae1df2a94d2ecc0eeb7e15123fca28ad0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58946462"
---
# <a name="idebugprogramnode2gethostname"></a>IDebugProgramNode2::GetHostName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft den Namen der Hostprozess für die Anwendung ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetHostName (   
   GETHOSTNAME_TYPE dwHostNameType,  
   BSTR*            pbstrHostName  
);  
```  
  
```csharp  
int GetHostName (   
   enum_GETHOSTNAME_TYPE dwHostNameType,  
   out string            pbstrHostName  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwHostNameType`  
 [in] Ein Wert aus der [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) -Enumeration, der den Typ der zur Rückgabe angibt.  
  
 `pbstrHostName`  
 [out] Gibt den Namen des Hostprozesses.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie Sie die Implementierung dieser Methode für eine einfache `CProgram` -Objekt, das macht die [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) Schnittstelle. In diesem Beispiel ignoriert die `dwHostNameType` Parameter und gibt nur den Namen des Programms aus der Basisname der Pfad des Moduls.  
  
```cpp#  
HRESULT CProgram::GetHostName(DWORD dwHostNameType, BSTR* pbstrHostName) {    
   // Check for valid argument.    
   if (pbstrHostName)    
   {    
      char szModule[_MAX_PATH];    
  
      // Attempt to assign to szModule the path for the file used  
      // to create the calling process.    
      if (GetModuleFileName(NULL, szModule, sizeof (szModule)))    
      {    
         // If successful then declare several char arrays    
         char  szDrive[_MAX_DRIVE];    
         char  szDir[_MAX_DIR];    
         char  szName[_MAX_FNAME];    
         char  szExt[_MAX_EXT];    
         char  szFilename[_MAX_FNAME + _MAX_EXT];    
         WCHAR wszFilename[_MAX_FNAME + _MAX_EXT];    
  
         // Break the szModule path name into components.    
         _splitpath(szModule, szDrive, szDir, szName, szExt);    
  
         // Copy the base file name szName into szFilename.    
         lstrcpy(szFilename, szName);    
         // Append the field extension szExt into szFilename.    
         lstrcat(szFilename, szExt);    
  
         // Convert the szFilename sequence of multibyte characters    
         // to the wszFilename sequence of wide characters.    
         mbstowcs(wszFilename, szFilename, sizeof (wszFilename) / 2);    
  
         // Assign the wszFilename to the value at *pbstrHostName.    
         *pbstrHostName = SysAllocString(wszFilename);    
  
          return S_OK;    
      }    
   }    
  
    return E_INVALIDARG;    
}    
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)

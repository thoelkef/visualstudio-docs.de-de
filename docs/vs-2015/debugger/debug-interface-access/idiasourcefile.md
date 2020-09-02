---
title: IDiaSourceFile | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile interface
ms.assetid: 6e9be757-797f-4960-ba62-c14092620bbd
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f8876febdae25c38d7cb637092d80dcac87f2418
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190613"
---
# <a name="idiasourcefile"></a>IDiaSourceFile
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Stellt eine Quelldatei dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaSourceFile : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDiaSourceFile` .  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDiaSourceFile::get_uniqueId](../../debugger/debug-interface-access/idiasourcefile-get-uniqueid.md)|Ruft einen einfachen ganzzahligen Schlüsselwert ab, der für dieses Bild eindeutig ist.|  
|[IDiaSourceFile::get_fileName](../../debugger/debug-interface-access/idiasourcefile-get-filename.md)|Ruft den Namen der Quelldatei ab.|  
|[IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)|Ruft den Prüfsummen Datentyp ab.|  
|[IDiaSourceFile::get_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)|Ruft einen Enumerator der Kompilierungen mit Zeilennummern ab, die auf diese Datei verweisen.|  
|[IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)|Ruft die Prüfsumme Bytes ab.|  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie diese Schnittstelle durch Aufrufen der [IDiaEnumSourceFiles:: Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md) -Methode oder der [IDiaEnumSourceFiles:: Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md) -Methode ab. Detail finden Sie in dem Beispiel.  
  
## <a name="example"></a>Beispiel  
 Diese Funktion zeigt die Namen aller Quelldateien an, die zur angegebenen Tabelle beitragen.  
  
```cpp#  
void ShowSourceFiles(IDiaTable *pTable)  
{  
    CComPtr<IDiaEnumSourceFiles> pSourceFiles;  
    if ( SUCCEEDED( pTable->QueryInterface(  
                                _uuidof( IDiaEnumSourceFiles ),  
                               (void**)&pSourceFiles )  
                  )  
       )  
    {  
        CComPtr<IDiaSourceFile> pSourceFile;  
        while ( SUCCEEDED( hr = pSourceFiles->Next( 1, &pSourceFile, &celt ) ) &&  
                celt == 1 )  
        {  
            CDiaBSTR fileName;  
            if ( pSourceFile->get_fileName( &fileName) == S_OK )  
            {  
                printf( "file name: %ws\n", fileName );  
            }  
            pSourceFile = NULL;  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumSourceFiles:: Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md)   
 [IDiaEnumSourceFiles:: Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md)   
 [IDiaLineNumber:: get_sourceFile](../../debugger/debug-interface-access/idialinenumber-get-sourcefile.md)   
 [IDiaSession:: findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)   
 [IDiaSession:: findLines](../../debugger/debug-interface-access/idiasession-findlines.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)

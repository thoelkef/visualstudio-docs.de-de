---
title: DisassemblyData | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DisassemblyData
helpviewer_keywords:
- DisassemblyData structure
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ea21b4ae9e6e852efcc3625dc3af24478bd88155
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58960964"
---
# <a name="disassemblydata"></a>DisassemblyData
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Beschreibt eine Disassembly-Anweisung für die integrierte Entwicklungsumgebung (IDE) angezeigt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct tagDisassemblyData {   
   DISASSEMBLY_STREAM_FIELDS dwFields;  
   BSTR                      bstrAddress;  
   BSTR                      bstrAddressOffset;  
   BSTR                      bstrCodeBytes;  
   BSTR                      bstrOpcode;  
   BSTR                      bstrOperands;  
   BSTR                      bstrSymbol;  
   UINT64                    uCodeLocationId;  
   TEXT_POSITION             posBeg;  
   TEXT_POSITION             posEnd;  
   BSTR                      bstrDocumentUrl;  
   DWORD                     dwByteOffset;  
   DISASSEMBLY_FLAGS         dwFlags;  
} DisassemblyData;  
```  
  
```csharp  
public struct DisassemblyData {   
   public uint          dwFields;  
   public string        bstrAddress;  
   public string        bstrAddressOffset;  
   public string        bstrCodeBytes;  
   public string        bstrOpcode;  
   public string        bstrOperands;  
   public string        bstrSymbol;  
   public ulong         uCodeLocationId;  
   public TEXT_POSITION posBeg;  
   public TEXT_POSITION posEnd;  
   public string        bstrDocumentUrl;  
   public uint          dwByteOffset;  
   public uint          dwFlags;  
};  
```  
  
## <a name="members"></a>Member  
 `dwFields`  
 Die [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) Konstante, die angibt, welche Felder ausgefüllt sind.  
  
 `bstrAddress`  
 Die Adresse als Offset von einem Startpunkt (in der Regel am Anfang der dazugehörigen).  
  
 `bstrCodeBytes`  
 Die Codebytes für diese Anweisung.  
  
 `bstrOpcode`  
 Der Opcode für diese Anweisung.  
  
 `bstrOperands`  
 Die Operanden für diese Anweisung.  
  
 `bstrSymbol`  
 Der Symbolname zugeordnet, wenn vorhanden, mit der Adresse (öffentlichen Symboldateien, Bezeichnung und So weiter).  
  
 `uCodeLocationId`  
 Der Bezeichner für diesen Speicherort disassembliert Zeile. Wenn die Adresse des Code-Kontext einer Zeile größer als die Adresse des Code-Kontext eines anderen ist, dann ist der disassemblierte Code Standortbezeichner des ersten auch größer als der Bezeichner des zweiten Speicherort.  
  
 `posBeg`  
 Die [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , entspricht der Position in einem Dokument, in denen die Disassembly Daten anfangen.  
  
 `posEnd`  
 Die [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , entspricht der Position in einem Dokument, in dem die Daten für die Disassemblierung beendet.  
  
 `bstrDocumentUrl`  
 Für Textdokumente, die als Dateiname dargestellt werden, können die `bstrDocumentUrl` gefüllt wird sich mit den Dateinamen, in die Quelle gefunden werden kann, mit dem Format `file://file name`.  
  
 Für Textdokumente, die als Dateiname dargestellt werden, können nicht `bstrDocumentUrl` ist ein eindeutiger Bezeichner für das Dokument und die Debug-Engine implementieren muss die [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md) Methode.  
  
 Dieses Feld kann auch weitere Informationen zu Prüfsummen enthalten. Einzelheiten finden Sie unter "Hinweise".  
  
 `dwByteOffset`  
 Die Anzahl der Bytes, die in die der Anweisung am Anfang der Codezeile ist.  
  
 `dwFlags`  
 Die [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) Konstante, die angibt, welche Flags aktiviert sind.  
  
## <a name="remarks"></a>Hinweise  
 Jede `DisassemblyData` Struktur beschreibt eine Anweisung der Disassemblierung. Ein Array dieser Strukturen wird zurückgegeben, aus der [lesen](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) Methode.  
  
 Die [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) Struktur textbasierte nur für Dokumente verwendet wird. Die Quelle des Bereichs für diese Anweisung ist nur für die erste Anweisung generiert, von einer Anweisung oder aus, z. B. ausgefüllt, wenn `dwByteOffset == 0`.  
  
 Für Dokumente, die kein Text sind ein Dokumentenkontext abgerufen werden kann, aus dem Code, und die `bstrDocumentUrl` Feld sollte ein null-Wert sein. Wenn die `bstrDocumentUrl` Feld ist identisch mit der `bstrDocumentUrl` Feld in der vorherigen `DisassemblyData` array-Element, und legen dann die `bstrDocumentUrl` auf den Wert null.  
  
 Wenn die `dwFlags` Feld verfügt über die `DF_DOCUMENT_CHECKSUM` flag so festgelegt, und dann zusätzliche Prüfsummeninformationen verweist Zeichenfolge folgt die `bstrDocumentUrl` Feld. Insbesondere folgt nach der null-Zeichenfolge-Terminator ist, gibt es eine GUID zum Identifizieren, die wiederum einen 4-Byte-Wert, der angibt, der Anzahl der Bytes der Prüfsumme folgt und wiederum folgt die Bytes der Prüfsumme, der Prüfsummenalgorithmus. Hier finden Sie im Beispiel in diesem Thema zum Codieren und Decodieren dieses Feld in [!INCLUDE[csprcs](../../../includes/csprcs-md.md)].  
  
## <a name="example"></a>Beispiel  
 Die `bstrDocumentUrl` Feld kann zusätzliche Informationen, die keine Zeichenfolge enthalten, wenn die `DF_DOCUMENT_CHECKSUM` -Flag festgelegt ist. Der Prozess zum Erstellen und diese codierte Zeichenfolge zu lesen ist unkompliziert [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)]. Allerdings [!INCLUDE[csprcs](../../../includes/csprcs-md.md)], es ist eine andere Sache. Für diejenigen, die anzeigen möchten, das folgende Beispiel zeigt eine Möglichkeit zum Erstellen der codierten Zeichenfolge aus [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] und eine Möglichkeit zum Decodieren der codierten Zeichenfolge in [!INCLUDE[csprcs](../../../includes/csprcs-md.md)].  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
  
namespace MyNamespace  
    class MyClass  
    {  
        string EncodeData(string documentString,  
                          Guid checksumGuid,  
                          byte[] checksumData)  
        {  
            string returnString = documentString;  
  
            if (checksumGuid == null || checksumData == null)  
            {  
                // Nothing more to do. Just return the string.  
                return returnString;  
            }  
  
            returnString += '\0'; // separating null value  
  
            // Add checksum GUID to string.  
            byte[] guidDataArray  = checksumGuid.ToByteArray();  
            int    guidDataLength = guidDataArray.Length;  
            IntPtr pBuffer        = Marshal.AllocCoTaskMem(guidDataLength);  
            for (int i = 0; i < guidDataLength; i++)  
            {  
                Marshal.WriteByte(pBuffer, i, guidDataArray[i]);  
            }  
            // Copy guid data bytes to string as wide characters.  
            // Assumption: sizeof(char) == 2.  
            for (int i = 0; i < guidDataLength; i++)  
            {  
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));  
            }  
  
            // Add checksum count (a 32-bit value).  
            Int32 checksumCount = checksumData.Length;  
            Marshal.StructureToPtr(checksumCount, pBuffer, true);  
            for (int i = 0; i < sizeof(Int32) / sizeof(char); i++)  
            {  
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));  
            }  
  
            // Add checksum data.  
            pBuffer = Marshal.AllocCoTaskMem(checksumCount);  
            for (int i = 0; i < checksumCount; i++)  
            {  
                Marshal.WriteByte(pBuffer, i, checksumData[i]);  
            }  
            for (int i = 0; i < checksumCount / sizeof(char); i++)  
            {  
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));  
            }  
            Marshal.FreeCoTaskMem(pBuffer);  
  
            return returnString;  
        }  
  
        void DecodeData(    string encodedString,  
                        out string documentString,  
                        out Guid   checksumGuid,  
                        out byte[] checksumData)  
       {  
           documentString = String.Empty;  
           checksumGuid = Guid.Empty;  
           checksumData = null;  
  
           IntPtr pBuffer = Marshal.StringToBSTR(encodedString);  
           if (null != pBuffer)  
           {  
               int bufferOffset = 0;  
  
               // Parse string out.  String is assumed to be Unicode.  
               documentString = Marshal.PtrToStringUni(pBuffer);  
               bufferOffset += (documentString.Length + 1) * sizeof(char);  
  
               // Parse Guid out.  
               // Read guid bytes from buffer and store in temporary  
               // buffer that contains only the guid bytes. Then the  
               // Marshal.PtrToStructure() can work properly.  
               byte[] guidDataArray  = checksumGuid.ToByteArray();  
               int    guidDataLength = guidDataArray.Length;  
               IntPtr pGuidBuffer    = Marshal.AllocCoTaskMem(guidDataLength);  
               for (int i = 0; i < guidDataLength; i++)  
               {  
                   Marshal.WriteByte(pGuidBuffer, i,  
                                     Marshal.ReadByte(pBuffer, bufferOffset + i);  
               }  
               bufferOffset += guidDataLength;  
               checksumGuid = (Guid)Marshal.PtrToStructure(pGuidBuffer, typeof(Guid));  
               Marshal.FreeCoTaskMem(pGuidBuffer);  
  
              // Parse out the number of checksum data bytes (always 32-bit value).  
              int dataCount = Marshal.ReadInt32(pBuffer, bufferOffset);  
              bufferOffset += sizeof(Int32);  
  
              // Parse out the checksum data.  
              checksumData = new byte[dataCount];  
              for (int i = 0; i < dataCount; i++)  
              {  
                  checksumData[i] = Marshal.ReadByte(pBuffer, bufferOffset + i);  
              }  
           }  
       }  
    }  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [Lesen](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)   
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)

---
title: "DisassemblyData | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DisassemblyData"
helpviewer_keywords: 
  - "DisassemblyData-Struktur"
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# DisassemblyData
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Beschreibt eine Demontagevorschrift für die integrierte Entwicklungsumgebung \(IDE\) anzuzeigen.  
  
## Syntax  
  
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
  
```c#  
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
  
## Mitglieder  
 `dwFields`  
 Die [DISASSEMBLY\_STREAM\_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) Konstante, die angibt, welche Felder geändert werden.  
  
 `bstrAddress`  
 Die Adresse als Offset einiger Anfangspunkt \(normalerweise der Beginn der mapped\-to\-Funktion\).  
  
 `bstrCodeBytes`  
 Die Bytes Code für diese Anweisung.  
  
 `bstrOpcode`  
 Der Opcode für diese Anweisung.  
  
 `bstrOperands`  
 Die Operanden für diese Anweisung.  
  
 `bstrSymbol`  
 Der Symbolname falls vorhanden\) mit der Adresse \(Public zugeordnete Symbol Bezeichnung usw.\).  
  
 `uCodeLocationId`  
 Der Speicherort des Codes Bezeichner für diese disassemblierte Zeile.  Wenn der Code Elementkontext adresse einer Zeile größer ist als die von anderen adresse Kontext des Codes ist, entspricht der Speicherort der Code disassemblierte Bezeichner größer als auch vom ersten Speicherort des Codes Bezeichner des zweiten Ausdrucks.  
  
 `posBeg`  
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) , das zur Position in einem Dokument entspricht, in der die Disassemblys von Daten begonnen wird.  
  
 `posEnd`  
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) , das zur Position in einem Dokument entspricht, in der die Disassemblys Daten beendet.  
  
 `bstrDocumentUrl`  
 Für Textdokumente, die als Dateiname dargestellt werden können, wird das `bstrDocumentUrl` Feld mit dem Dateinamen, in dem die Quelle in das Format gefunden werden kann `file://file-Name`aufgefüllt.  
  
 Für Textdokumente, die nicht als Dateiname dargestellt werden können, ist `bstrDocumentUrl` ein eindeutiger Bezeichner für das Dokument, und das Debugmodul muss die [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)\-Methode implementieren.  
  
 Dieses Feld kann zusätzliche Informationen zu Prüfsummen enthalten.  Weitere Informationen finden Sie in den Hinweisen.  
  
 `dwByteOffset`  
 Die Anweisung ist die Anzahl der Bytes vom Anfang der Zeile.  
  
 `dwFlags`  
 Die [DISASSEMBLY\_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) Konstante, die angibt, welche Flags aktiv sind.  
  
## Hinweise  
 Jede `DisassemblyData` Struktur beschreibt eine Anweisung der Disassemblys.  Ein Array von dieser Strukturen [Lesen](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) wird von der Methode zurückgegeben.  
  
 Die [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) Struktur wird nur für Basisdokumente von Text verwendet.  Der Bereich Quellcode für diese Anweisung wird nur für die erste Anweisung ergänzt, die von einer Anweisung oder einer Zeile z. B. wenn `dwByteOffset == 0`generiert wird.  
  
 Für Dokumente, die nicht\-Text sind, kann ein Dokumentenkontext im Code abgerufen werden, und das `bstrDocumentUrl` Feld muss ein NULL\-Wert sein.  Wenn das Feld `bstrDocumentUrl` dasselbe wie das `bstrDocumentUrl` Feld im vorherigen `DisassemblyData` Arrayelement ist, legen Sie `bstrDocumentUrl` auf einen NULL\-Wert festgelegt.  
  
 Wenn das `dwFlags` Feld das `DF_DOCUMENT_CHECKSUM`\-Flag aufweist, führen weitere Informationen zu Prüfsummen durch den der Zeichenfolge, die `bstrDocumentUrl` Feld dargestellt wird.  Insbesondere nach dem NULL\-Zeichenfolgen\-Abschlusszeichen, folgt eine GUID, die den Prüfsummenalgorithmus bezeichnet, der wiederum durch einen 4\-Byte\-Wert folgt, der die Anzahl der Bytes in der Prüfsumme angibt und der wiederum von Prüfsummen Bytes folgt.  Weitere Informationen finden Sie im Beispiel in diesem Thema aufgelistet, wie Sie dieses Feld in [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]codiert und decodiert.  
  
## Beispiel  
 Das Feld kann zusätzliche Informationen `bstrDocumentUrl` anders als eine Zeichenfolge enthalten, wenn das `DF_DOCUMENT_CHECKSUM`\-Flag festgelegt ist.  Der Prozess des Erstellens und das Lesen dieser codierten Zeichenfolge ist in [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)]einfach.  In [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)], ist es ein anderer Stoff.  Für diejenigen, die neugierig sind, werden im folgenden Beispiel eine Möglichkeit, die codierte Zeichenfolge aus [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] zu erstellen und eine Möglichkeit dargestellt, die codierte Zeichenfolge in [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]zu decodieren.  
  
```c#  
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
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [Lesen](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY\_STREAM\_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)   
 [DISASSEMBLY\_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
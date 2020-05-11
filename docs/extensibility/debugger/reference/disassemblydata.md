---
title: DemontageDaten | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DisassemblyData
helpviewer_keywords:
- DisassemblyData structure
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9dcf3316ba57bbb25ee171cba7e4edc4923fa270
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737286"
---
# <a name="disassemblydata"></a>DisassemblyData
Beschreibt eine Demontageanweisung für die anzuzeigende integrierte Entwicklungsumgebung (IDE).

## <a name="syntax"></a>Syntax

```cpp
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
`dwFields`\
Die [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) Konstante an, die angibt, welche Felder ausgefüllt werden.

`bstrAddress`\
Die Adresse als Offset von einem Startpunkt (in der Regel der Anfang der zugeordneten Funktion).

`bstrCodeBytes`\
Die Codebytes für diese Anweisung.

`bstrOpcode`\
Der Opcode für diese Anweisung.

`bstrOperands`\
Die Operanden für diese Anweisung.

`bstrSymbol`\
Der Symbolname, falls vorhanden, ist der Adresse zugeordnet (öffentliches Symbol, Beschriftung usw.).

`uCodeLocationId`\
Der Codepositionsbezeichner für diese zerlegte Zeile. Wenn die Codekontextadresse einer Zeile größer als die Codekontextadresse einer anderen Zeile ist, ist der disassemblierte Codespeicherortbezeichner der ersten Zeile auch größer als der Codespeicherortbezeichner der zweiten Zeile.

`posBeg`\
Die [TEXT_POSITION,](../../../extensibility/debugger/reference/text-position.md) die der Position in einem Dokument entspricht, in dem die Demontagedaten beginnen.

`posEnd`\
Die [TEXT_POSITION,](../../../extensibility/debugger/reference/text-position.md) die der Position in einem Dokument entspricht, an der die Demontagedaten enden.

`bstrDocumentUrl`\
Bei Textdokumenten, die als Dateinamen `bstrDocumentUrl` dargestellt werden können, wird das Feld mit dem `file://file name`Dateinamen ausgefüllt, in dem sich die Quelle befindet, und verwendet das Format .

Für Textdokumente, die nicht als `bstrDocumentUrl` Dateinamen dargestellt werden können, ist ein eindeutiger Bezeichner für das Dokument, und das Debugmodul muss die [GetDocument-Methode](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md) implementieren.

Dieses Feld kann auch zusätzliche Informationen zu Prüfsummen enthalten. Einzelheiten finden Sie in den Hinweisen.

`dwByteOffset`\
Die Anzahl der Bytes, die die Anweisung vom Anfang der Codezeile entfernt hat.

`dwFlags`\
Die [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) Konstante an, die angibt, welche Flags aktiv sind.

## <a name="remarks"></a>Bemerkungen
Jede `DisassemblyData` Struktur beschreibt eine Anweisung der Demontage. Ein Array dieser Strukturen wird von der [Read-Methode](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) zurückgegeben.

Die [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) Struktur wird nur für textbasierte Dokumente verwendet. Der Quellcodebereich für diese Anweisung wird nur für die erste Anweisung ausgefüllt, `dwByteOffset == 0`die aus einer Anweisung oder Zeile generiert wird, z. B. wenn .

Bei Dokumenten, die nicht textuell sind, kann ein Dokumentkontext `bstrDocumentUrl` aus dem Code abgerufen werden, und das Feld sollte ein Nullwert sein. Wenn `bstrDocumentUrl` das Feld mit `bstrDocumentUrl` dem Feld `DisassemblyData` im vorherigen Arrayelement `bstrDocumentUrl` identisch ist, legen Sie den Aufeinen auf null Wert fest.

Wenn `dwFlags` für das `DF_DOCUMENT_CHECKSUM` Feld das Flag festgelegt ist, folgen zusätzliche `bstrDocumentUrl` Prüfsummeninformationen der Zeichenfolge, auf die das Feld zeigt. Insbesondere folgt nach dem Null-Zeichenfolgen-Terminator eine GUID, die den Prüfsummenalgorithmus identifiziert, gefolgt von einem 4-Byte-Wert, der die Anzahl der Bytes in der Prüfsumme angibt und auf die wiederum die Prüfsummenbytes folgen. Im Beispiel in diesem Thema zum Codieren und [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]Decodieren dieses Felds in .

## <a name="example"></a>Beispiel
Das `bstrDocumentUrl` Feld kann zusätzliche Informationen enthalten, `DF_DOCUMENT_CHECKSUM` die nicht eine Zeichenfolge sind, wenn das Flag festgelegt ist. Das Erstellen und Lesen dieser codierten Zeichenfolge [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)]ist in einfach. In [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]aber ist es eine andere Sache. Für Neugierige zeigt das folgende Beispiel eine Möglichkeit zum Erstellen [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] der codierten Zeichenfolge aus und [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]eine Möglichkeit, die codierte Zeichenfolge in zu dekodieren.

```csharp
using System;
using System.Runtime.InteropServices;

namespace MyNamespace
{
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
            for (int i = 0; i < guidDataLength / sizeof(char); i++)
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

                // Parse string out. String is assumed to be Unicode.
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
                                      Marshal.ReadByte(pBuffer, bufferOffset + i));
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

## <a name="see-also"></a>Weitere Informationen
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [Lesen](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)

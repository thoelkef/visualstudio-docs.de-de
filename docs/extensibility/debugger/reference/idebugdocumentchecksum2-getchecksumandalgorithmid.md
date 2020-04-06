---
title: IDebugDocumentChecksum2::GetChecksumAndAlgorithmId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentChecksum2::GetChecksumAndAlgorithmI
- GetChecksumAndAlgorithmI
ms.assetid: 25efef99-0ef3-4332-a752-607605fc6e67
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c26d5b9c2c45fd1ce932fc1108e4f77f2508cb31
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731941"
---
# <a name="idebugdocumentchecksum2getchecksumandalgorithmid"></a>IDebugDocumentChecksum2::GetChecksumAndAlgorithmId
Ruft die Dokumentprüfsumme und den Algorithmusbezeichner anhand der maximal zu verwendenden Anzahl von Bytes ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetChecksumAndAlgorithmId(
    GUID  *pRetVal,
    ULONG cMaxBytes,
    BYTE  *pChecksum,
    ULONG *pcNumBytes
);
```

```csharp
public int GetChecksumAndAlgorithmId(
    out Guid pRetVal,
    uint     cMaxBytes,
    out byte pChecksum,
    out uint pcNumBytes
);
```

## <a name="parameters"></a>Parameter
`pRetVal`\
[out] Eindeutiger Bezeichner für den Prüfsummenalgorithmus.

`cMaxBytes`\
[in] Maximale Anzahl von Bytes, die für die Prüfsumme verwendet werden sollen.

`pChecksum`\
[out] Wert der Prüfsumme.

`pcNumBytes`\
[out] Tatsächliche Anzahl der Bytes, die für die Prüfsumme verwendet werden.

## <a name="return-value"></a>Rückgabewert
Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="example"></a>Beispiel
Im folgenden Beispiel wird diese Methode verwendet, um die Prüfsumme und den Algorithmus für ein Dokument abzubekommen.

```cpp
HRESULT CDebugCodeContext::GetDocumentChecksumAndAlgorithmId(GUID *pguidAlgorithm, BYTE **ppChecksum, ULONG *pcNumBytes)
{
    HRESULT hRes = E_FAIL;

    *ppChecksum = NULL;
    *pcNumBytes = 0;

    CComPtr<IDebugDocumentContext2> pDocContext;

    hRes = this->GetDocumentContext(&pDocContext);

    if ( HREVAL(S_OK, hRes) )
    {
        CComQIPtr<IDebugDocumentChecksum2> pDocChecksum(pDocContext);

        if ( pDocChecksum != NULL )
        {
            // Figure out the size of the checksum buffer required
            ULONG cNumBytes = 0;

            hRes = pDocChecksum->GetChecksumAndAlgorithmId(pguidAlgorithm, 0, NULL, &cNumBytes);

            if ( S_OK == hRes )
            {
                // check to see if we got back valid values
                if ( cNumBytes && GUID_NULL != (*pguidAlgorithm) )
                {
                    // Alloc space for the checksum data
                    BYTE *pChecksum = (BYTE*) CoTaskMemAlloc(cNumBytes);

                    if ( pChecksum )
                    {
                        // Get the buffer containing the checksum info
                        hRes = pDocChecksum->GetChecksumAndAlgorithmId(pguidAlgorithm, cNumBytes, pChecksum, &cNumBytes);

                        if ( HREVAL(S_OK, hRes) )
                        {
                            *ppChecksum = pChecksum;
                            *pcNumBytes = cNumBytes;
                        }
                        else
                        {
                            CoTaskMemFree(pChecksum);
                        }
                    }
                    else
                        hRes = E_OUTOFMEMORY;
                }
                else
                    hRes = S_FALSE; // lang doesn't support checksums
            }
            else
                hRes = S_FALSE; // failed to work out checksum info
        }
        else
            hRes = S_FALSE; // SH doesn't support checksums
    }

    return ( hRes );
}
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)

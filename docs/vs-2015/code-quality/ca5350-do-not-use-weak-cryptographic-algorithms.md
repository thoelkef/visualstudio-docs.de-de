---
title: 'CA5350: Verwenden Sie keine schwache kryptografische Algorithmen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 4c51bb8a-fcfa-46aa-ab61-634be84c4a7a
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2997abd9a112b60e9ef692bfe87b740976007656
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58959850"
---
# <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a>CA5350: Keine schwachen Kryptografiealgorithmen verwenden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotUseWeakCryptographicAlgorithms|  
|CheckId|CA5350|  
|Kategorie|Microsoft.Cryptography|  
|Unterbrechende Änderung|Nicht unterbrechende Änderung|  
  
> [!NOTE]
>  Diese Warnung wurde zuletzt im November 2015 aktualisiert.  
  
## <a name="cause"></a>Ursache  
 Verschlüsselungsalgorithmen, wie z. B. <xref:System.Security.Cryptography.TripleDES> , und Hashalgorithmen, wie z. B. <xref:System.Security.Cryptography.SHA1> und <xref:System.Security.Cryptography.RIPEMD160> , gelten als schwach.  
  
 Diese kryptografischen Algorithmen bieten nicht dieselbe Sicherheitsgarantie wie modernere Entsprechungen. Die kryptografischen Hashalgorithmen <xref:System.Security.Cryptography.SHA1> und <xref:System.Security.Cryptography.RIPEMD160> bieten weniger Resistenz gegenüber Konflikten als modernere Hashalgorithmen. Der Verschlüsselungsalgorithmus <xref:System.Security.Cryptography.TripleDES> bietet weniger Sicherheit als modernere Verschlüsselungsalgorithmen.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Unsichere Verschlüsselungsalgorithmen und Hashfunktionen werden heute aus verschiedenen Gründen verwendet, sollten jedoch nicht verwendet werden, um die Vertrauenswürdigkeit der Daten, die sie schützen, zu gewährleisten.  
  
 Die Regel wird beim Auffinden von 3DES-, SHA1- oder RIPEMD160-Algorithmen im Code ausgelöst und gibt eine Warnung für den Benutzer zurück.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Verwenden Sie kryptografisch sicherere Optionen:  
  
-   Verwenden Sie für TripleDES-Verschlüsselung die <xref:System.Security.Cryptography.Aes> -Verschlüsselung.  
  
-   Verwenden Sie für SHA1- oder RIPEMD160-Hashfunktionen diejenigen der [SHA-2](https://msdn.microsoft.com/library/windows/desktop/aa382459.aspx) -Produktfamilie (z. B. <xref:System.Security.Cryptography.SHA512>, <xref:System.Security.Cryptography.SHA384>, <xref:System.Security.Cryptography.SHA256>).  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel, wenn der für die Daten benötigte Schutzgrad keine Sicherheitsgarantie erfordert.  
  
## <a name="pseudo-code-example"></a>Pseudocodebeispiel  
 Zum Zeitpunkt der Erstellung dieses Dokuments veranschaulicht das folgende Beispiel mit Pseudocode das von dieser Regel erkannte Muster.  
  
### <a name="sha-1-hashing-violation"></a>Verstoß bei SHA-1-Hashfunktion  
  
```  
using System.Security.Cryptography;   
...   
var hashAlg = SHA1.Create();  
  
```  
  
### <a name="solution"></a>Lösung  
  
```  
using System.Security.Cryptography;   
...   
var hashAlg = SHA256.Create();  
  
```  
  
### <a name="ripemd160-br-br-hashing-violation"></a>RIPEMD160 <br /><br />Verletzung Hashing  
  
```  
using System.Security.Cryptography;   
...   
var hashAlg = RIPEMD160Managed.Create();  
  
```  
  
### <a name="solution"></a>Lösung  
  
```  
using System.Security.Cryptography;   
...   
var hashAlg = SHA256.Create();  
  
```  
  
### <a name="tripledes-encryption-violation"></a>Verstoß bei TripleDES-Verschlüsselung  
  
```  
using System.Security.Cryptography;   
...    
using (TripleDES encAlg = TripleDES.Create())   
{   
  ...   
}  
```  
  
### <a name="solution"></a>Lösung  
  
```  
using System.Security.Cryptography;   
...   
using (AesManaged encAlg = new AesManaged())   
{   
  ...   
}  
```
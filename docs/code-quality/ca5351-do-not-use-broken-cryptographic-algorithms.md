---
title: CA5351 Verwenden Sie keine unterbrochene kryptografische Algorithmen. | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 483f51b3-e186-4433-b48e-5ca24a9a9c94
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: fd9959fe67097b815a4a86b81b5cf78e468281a5
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2018
---
# <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a>CA5351 Verwenden Sie keine unterbrochenen kryptografischen Algorithmen.
|||  
|-|-|  
|TypeName|DoNotUseBrokenCryptographicAlgorithms|  
|CheckId|CA5351|  
|Kategorie|Microsoft.Cryptography|  
|Unterbrechende Änderung|Nicht unterbrechende Änderung|  
  
> [!NOTE]
>  Diese Warnung wurde zuletzt im November 2015 aktualisiert.  
  
## <a name="cause"></a>Ursache  
 Hashfunktionen wie <xref:System.Security.Cryptography.MD5> und Verschlüsselungsalgorithmen wie <xref:System.Security.Cryptography.DES> und <xref:System.Security.Cryptography.RC2> können ein erhebliches Risiko darstellen und führen möglicherweise zur Enthüllung vertraulicher Informationen mithilfe einfacher Angriffsstrategien, wie z. B. Brute-Force-Angriffe und Kollisionsangriffe gegen Hashfunktionen.  
  
 Die kryptografischen Algorithmen in der folgenden Liste sind anfällig für bekannte kryptografische Angriffe. Der kryptografische Hashalgorithmus <xref:System.Security.Cryptography.MD5> ist anfällig für Kollisionsangriffe gegen Hashfunktionen.  Je nach Einsatzbereich führen Kollisionsangriffe gegen Hashfunktionen zu Identitätswechseln, Manipulationen oder anderen Arten von Angriffen auf Systeme, die auf der eindeutigen kryptografischen Ausgabe einer Hashfunktion beruhen. Die Verschlüsselungsalgorithmen <xref:System.Security.Cryptography.DES> und <xref:System.Security.Cryptography.RC2> sind anfällig für kryptografische Angriffe, die zu einer unbeabsichtigten Offenlegung von verschlüsselten Daten führen können.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Unterbrochene kryptografische Algorithmen werden nicht als sicher betrachtet; ihre Verwendung sollte unterbunden werden. Der MD5-Hashalgorithmus ist anfällig für bekannte Kollisionsangriffe. Die spezielle Sicherheitslücke hängt jedoch vom Verwendungszusammenhang ab.  Zum Sicherstellen der Datenintegrität (z. B. Dateisignatur oder digitales Zertifikat) verwendete Hashalgorithmen sind besonders anfällig.  In diesem Kontext könnten Angreifer zwei separate Teile der Daten generieren und nützliche Daten durch schädliche Daten ersetzen, ohne den Hashwert zu ändern oder eine zugeordnete digitale Signatur für ungültig zu erklären.  
  
 Bei Verschlüsselungsalgorithmen:  
  
-   Die<xref:System.Security.Cryptography.DES> -Verschlüsselung enthält eine kleine Schlüsselgröße, die in weniger als einem Tag einem Brute-Force-Angriff zum Opfer fallen könnte.  
  
-   Die<xref:System.Security.Cryptography.RC2> -Verschlüsselung ist anfällig für einen schlüsselbezogenen Angriff, bei dem der Angreifer nach mathematischen Beziehungen zwischen allen Schlüsselwerten sucht.  
  
 Diese Regel löst aus, wenn eine der oben genannten Kryptografiefunktionen im Quellcode gefunden wird, und gibt eine Warnung für den Benutzer aus.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Verwenden Sie kryptografisch sicherere Optionen:  
  
-   Verwenden Sie für MD5-Hashes in der [SHA-2](https://msdn.microsoft.com/library/windows/desktop/aa382459.aspx) Familie (z. B. <xref:System.Security.Cryptography.SHA512>, <xref:System.Security.Cryptography.SHA384>, <xref:System.Security.Cryptography.SHA256>).  
  
-   Verwenden Sie für DES und RC2 eine <xref:System.Security.Cryptography.Aes> -Verschlüsselung.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel, bevor sie von einem Kryptografie-Experten geprüft wurde.  
  
## <a name="pseudo-code-example"></a>Pseudocodebeispiel  
 Das folgende Beispiel mit Pseudocode veranschaulicht das von dieser Regel erkannte Muster und mögliche Alternativen.  
  
### <a name="md5-hashing-violation"></a>Verstoß bei MD5-Hashfunktion  
  
```  
using System.Security.Cryptography;   
...   
var hashAlg = MD5.Create();  
  
```  
  
### <a name="solution"></a>Lösung  
  
```  
using System.Security.Cryptography;   
...   
var hashAlg = SHA256.Create();  
  
```  
  
### <a name="rc2-encryption-violation"></a>Verstoß bei RC2-Verschlüsselung  
  
```  
using System.Security.Cryptography;   
...    
RC2 encAlg = RC2.Create();  
  
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
  
### <a name="des-br-br-encryption-violation"></a>DES <br /><br />Verstoß bei Verschlüsselung  
  
```  
using System.Security.Cryptography;   
...   
DES encAlg = DES.Create();  
  
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
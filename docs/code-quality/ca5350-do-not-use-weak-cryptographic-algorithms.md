---
title: "CA5350: Verwenden Sie keine schwachen kryptografischen Algorithmen. | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c51bb8a-fcfa-46aa-ab61-634be84c4a7a
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA5350: Verwenden Sie keine schwachen kryptografischen Algorithmen.
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotUseWeakCryptographicAlgorithms|  
|CheckId|CA5350|  
|Kategorie|Microsoft.Cryptography|  
|Unterbrechende Änderung|Nicht unterbrechende Änderung|  
  
> [!NOTE]
>  Diese Warnung wurde zuletzt im November 2015 aktualisiert.  
  
## Ursache  
 Verschlüsselungsalgorithmen, wie z. B. <xref:System.Security.Cryptography.TripleDES>, und Hashalgorithmen, wie z. B. <xref:System.Security.Cryptography.SHA1> und <xref:System.Security.Cryptography.RIPEMD160>, gelten als schwach.  
  
 Diese kryptografischen Algorithmen bieten nicht dieselbe Sicherheitsgarantie wie modernere Entsprechungen. Die kryptografischen Hashalgorithmen <xref:System.Security.Cryptography.SHA1> und <xref:System.Security.Cryptography.RIPEMD160> bieten weniger Resistenz gegenüber Konflikten als modernere Hashalgorithmen. Der Verschlüsselungsalgorithmus <xref:System.Security.Cryptography.TripleDES> bietet weniger Sicherheit als modernere Verschlüsselungsalgorithmen.  
  
## Regelbeschreibung  
 Unsichere Verschlüsselungsalgorithmen und Hashfunktionen werden heute aus verschiedenen Gründen verwendet, sollten jedoch nicht verwendet werden, um die Vertrauenswürdigkeit der Daten, die sie schützen, zu gewährleisten.  
  
 Die Regel wird beim Auffinden von 3DES\-, SHA1\- oder RIPEMD160\-Algorithmen im Code ausgelöst und gibt eine Warnung für den Benutzer zurück.  
  
## Behandeln von Verstößen  
 Verwenden Sie kryptografisch sicherere Optionen:  
  
-   Verwenden Sie für TripleDES\-Verschlüsselung die <xref:System.Security.Cryptography.Aes>\-Verschlüsselung.  
  
-   Verwenden Sie für SHA1\- oder RIPEMD160\-Hashfunktionen diejenigen der [SHA\-2](https://msdn.microsoft.com/en-us/library/windows/desktop/aa382459.aspx)\-Produktfamilie \(z. B. <xref:System.Security.Cryptography.SHA512>, <xref:System.Security.Cryptography.SHA384>, <xref:System.Security.Cryptography.SHA256>\).  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel, wenn der für die Daten benötigte Schutzgrad keine Sicherheitsgarantie erfordert.  
  
## Pseudocodebeispiel  
 Zum Zeitpunkt der Erstellung dieses Dokuments veranschaulicht das folgende Beispiel mit Pseudocode das von dieser Regel erkannte Muster.  
  
### Verstoß bei SHA\-1\-Hashfunktion  
  
```  
using System.Security.Cryptography; ... var hashAlg = SHA1.Create();  
  
```  
  
### Lösung  
  
```  
using System.Security.Cryptography; ... var hashAlg = SHA256.Create();  
  
```  
  
### Verstoß bei RIPEMD160\-Hashfunktion  
  
```  
using System.Security.Cryptography; ... var hashAlg = RIPEMD160Managed.Create();  
  
```  
  
### Lösung  
  
```  
using System.Security.Cryptography; ... var hashAlg = SHA256.Create();  
  
```  
  
### Verstoß bei TripleDES\-Verschlüsselung  
  
```  
using System.Security.Cryptography; ... using (TripleDES encAlg = TripleDES.Create()) { ... }  
```  
  
### Lösung  
  
```  
using System.Security.Cryptography; ... using (AesManaged encAlg = new AesManaged()) { ... }  
```
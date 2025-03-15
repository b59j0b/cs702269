java c
CSCI-GA.3033-107: Cryptography of Blockchains
Spring 2024
Homework #2
Due: 11:59pm on Sunday, 3/10, 2024
Submit via Brightspace
Problem 1. Distributed Randomness Beacons using VDFs. A distributed randomness beacon(DRB) allows mutually untrusted parties to engage in a protocol and derive a random value ω thatcannot be biased by any party. Consider the verifiable delay function VDF(x) : G → G = x2twhere (G, ·) is a multiplicative group of unknown order. Let g be a generator of G and leth = VDF(g). Consider the following one-round protocol DRB1:Round 1: Each party reveals a random value ri.Suppose n parties participate in Round 1. The DRB output is obtained as ω = (!ni=1ri)2t∈ G.a. Show that this protocol is not secure and can be biased. That is, describe an attack anadversary acting as of the parties can perform. that lets them set the DRB output to anyvalue they want. (Note the adversary can get preparation time before the protocol starts.)b. Suggest a solution to this attack based on the solution used to prevent the rogue-key attackwhen aggregating BLS signatures. (You need not prove your answer. A brief justification isenough.)An issue with the VDF-based DRBs is that they always require a costly VDF computationto be done. Consider the following protocol DRB2:Round 1: Commit Round: Each party i samples a random nonce αi and shares ci = gαi .Round 2: Reveal Round: After all parties share their commitments, each party reveals αi. (Ifci = gαi then this αi is ignored by the other parties).Suppose n parties participate in Round 1. There are two scenarios here, based on the behavior.of the n parties in Round 2. The optimistic scenario allows all the parties to compute theoutput quickly while the pessimistic one resorts to the costly VDF computation.• Optimistic case: If all n parties reveal a valid nonce in Round 2, then the DRB outputω is quickly obtained as ω = !ni=1hαi .• Pessimistic case: If any party skips Round 2, then the DRB output is obtained by theothers as ω = VDF(!ni=1ci).(You may verify that the randomness obtained in the two cases is the same.)c. This scheme also suffers from a biasing attack similar to the one in part (a). Show how.d. As in part (b), write out a solution that prevents the above attack. (Again, it’s based on thetechnique used in BLS signature aggregation. And you need not formally prove security.)e. Even after this fix, there is an inherent weakness associated with any DRB that has an“optimistic” fast case and a “pessimistic” slow case. Show how one party participating in theprotocol can learn ω much faster than all the other parties. (Note that they don’t bias thevalue. They only learn it much faster than the others.)1Problem 2. More VDFsa. Is Proof-of-Work a VDF? Why or why not? If it is, describe the VDF input, output, andprove and verify functions. If not, describe what property of a VDF is not satisfied.b. Can a VDF be used as a Proof-of-Work function? For a given challenge ch, the goal of theminer to now produce a valid output and proof for a given VDF function on input ch.c. A commonly used randomness beacon is the Bitcoin blockchain. Suppose random value ris obtained by hashing the latest block header b as r = H(b). What is one issue with thismethod? (Hint: think ab代 写CSCI-GA. 3033-107: Cryptography of Blockchains Spring 2024 Homework #2
代做程序编程语言out which parties can bias the randomness.)d. What if the randomness is obtained by hashing the VDF output on the header, instead? Thatis, r = H(VDF(b)). Briefly explain (doesn’t have to be formal) how this is secure or insecure.Problem 3. Certificates of CorrectnessIn class, we so far have seen ways to obtain quorum certificates where each signature has equalweight. What if we want to extend this to a scenario where different nodes have different weights?This may be the scenario in a Proof-of-Stake blockchain where the more stake you have, the moreyour vote counts. Instead of needing 2/3rd of all miners for a quorum, you need 2/3rd of all theweight (that is, stake).a. Let node i have weight wi for i = 1, . . . , n. Modify the Merkle tree construction for QC toshow that some fraction x of all stake is in the quorum. Hint: Assume the total stake isT = "ni=1wi. The Merkle tree should enable the verifier to query a value q between 0 and Tand the prover returns the leaf wi′, such that "i′−1i=1wi < q and "i′i=1wi >= q. The Merkletree needs to track more information than just the hashes in order to do this.Problem 4. Security of Wesolowski VDFThis question will analyze the role of the prime challenge ℓ in Wesolowski VDFs. To establishnotation, the input is (G, g, h,t), w here g, h ∈ G and the prover claim is that h = g2t. Theverifier sends a challenge ℓ, which is a prime. The prover responds π where π = gq and 2t = qℓ+rand r < ℓ. Thea. Show that the scheme isn’t secure when ℓ ≈ 2λ is the product of small primes each less thank (for some constant k), by describing an attack that runs in time O(k · λ) group operations.Problem 5. Batching Polynomial CommitmentsIn this question, we’ll build and efficient batch evaluation proofs from a linearly homomorphic polynomial commitment scheme. Here, a prover P and verifier V have input polynomialsf0, . . . , fℓ−1 ∈ F
         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com

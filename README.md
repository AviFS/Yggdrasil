# Yggdrasil
A self-modifying esoteric language based around binary trees

[Try it online!](https://tio.run/##3Vhdd6M2EH3nV6jpNkCMnXj7RpPd/oCePu1bTkIVkGNO@ToCp5vTdP@6OyMhIyyJmGz6Up@TGKOZO3euRtJA89xt6@rnfV42Ne9I@9x66rLjefXoeWldlrTKknRLeUtuiO/7Z/4v158WF8vL@/OX@OYz3DGsirztgpI2Qc2ziIxGw9DzOs7YwXY0CgEL2rbkC1jEHuk/GduQJMmrvEuSoGXFJiK8rruIFGzTAcTvdcXgVv64Vb/CwVl90G@FbmCCX3aDHhG/HAh9FPHtHVHkrOE9RQsDzrodr4gf/P1PRORf6K82NS9pFxzoRQORSAsZKml@Y3QToD7hpEAFmLlUwDFIQU94lJsuFdq@LU1B1EhR8PI8BMLbCdZCQDmnzxHBa3MC840cyFsxYgbs3b4ckFZN3QRXUGnKQsfK27xqO1qlLEDHSAjqTgNtPN2/AllElNNd8IYUus@BQMG7QKo6w2z0RAwbQQPMchlMrp1YuQoh8Np0ZEXLDnZigux2hnC61qpmjPk7EUspIsvt/yGJWjoOTTxrieAiaFmXoE3bV@MTLdpx8Z9asEOh0Y17sQysn2PFRmSNgY2FY4j1NWVNN3a0TIae5atloC8M2@IGnnrVvU5WkTS8NKZy1nWL8UT0@6@YDW9eJU/loMpkZhIjN3sWw949SkPcVnm4q7Dj9InxlgVpmbVyI35bEUpkLdKuShBTA1b/b@80RhYCYgrCSQt1MmIKj5D4ZlcUyQMHmtvge3Mg6ZYHhwUVeq5RPCdDsrDGlym4BnX2g04wdxEpWVlz2D3SHeeskjMakYbiD0g@rzL2FSb7SmOPG55opzJ2K8bvrMefNINGbuWbmTfQ9HUBg534RiSoh5eJhlass7lYqMsE4Jl/NpccajlFMX4Piu9D5YOTiqn39Bxe25Bkkaxo0wDBEaSZiD6KuRwLYI366b@MKvtqW9g/LGGPkBQL3FRDz4ryzY@JITO4fjNuWt1/dbhf2aMtHOb2SoONwlFJVvDlPPDlLPCLeeAXs8Av54FfXs5Cv5@Hfj8L/Hwe@Pks8Jd54C9OcCv6jW0BwZkDAY7PJyOg7RAzg1s6wfH5bz/XRp2Azviz725zMU93e3vyxjZqpd4Ed/QmQOf/43vxl7o5rft9DwxvXzn1AwujNqWVeLVjjGTQgm5haG1mITqQhW3or21eMHji2k3oiZSGRkUx6@NZUSc8w4Pn8hXPPh/YrmPywBn902ksNFnY26kZWkBMRJp6DOu7WjRT68Ps1EUI2SmWNK/6LpHyx6dxi4svJ3BMPaGNusPRm7mClg8ZJWksn75RViFm4oulQGoOp3gI@3qQkh/g/k9@GAloramRbEcPHcPzr3zb15P0Tqtrax0fmt1BFVlicuCaFEwKYnsm7n3f0F7jjrf2vBxfeFW0ZEki9UlwApJEW0diRnzf3y@S5MMeLm7X8XJ9Fw1iM3j@ivD16grVgOG7MAz3@/X@478 "Python 3 – Try It Online")


---

Yggdrasil treats its source code and its memory as the same. The memory model used by Yggdrasil is a [full binary tree](https://en.wikipedia.org/wiki/Binary_tree#Types_of_binary_trees), where each node is established initially by the source code. The characters `"';<>+*-/^&|:=?` are binary nodes, and take the next two nodes as their children. Every other character is a *leaf* node with no children. For example, `;<ab>+cd?e.` has the following binary tree:

           ;
        /     \
       /       \
      <         >
     / \     /     \  
    a   b   +       ?
           / \     /  \
          /   \   /    \
         c     d e      .
         
 Yggdrasil technically stores each character in the tree as it's Unicode code point, and treats strings as lists of code points. Before turning the source code into a tree however, Yggdrasil makes 2 substitutions:
 
- All `%` in the source code are replaced with NULL bytes
- Each `_` is repalced by the seqeuntial command line arguments, with missing arguments filled with 0

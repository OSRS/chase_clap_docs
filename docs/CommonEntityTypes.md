Common Entity Types

Entity - uuid:{596C69C3-B202-4316-9B99-7C427C8186E0}
    parent: NULL

CommunityEntity - uuid:{3F35074E-02E4-4517-8D49-628659925786}
    parent: Entity

Community - uuid:{80D8CC26-1BB2-4750-B348-0F47DC842143}
    parent: CommunityEntity

Organization - uuid:{F5C5A252-6D2C-4D6B-8A54-2A0619652C6A}
    parent: CommunityEntity

Person - uuid:{C43AE6B9-4A52-4766-B229-8CF9D491E90D}
    parent: CommunityEntity

Tag - uuid:{53D829F5-403E-4905-83D5-D8A43ABA747D}
    parent: Entity

Feature - uuid:{9A4ED95D-A44E-4979-AB04-01074C5B0C3E}
    parent: Entity

CommunityOwnedEntity - uuid:{48B5CD5B-7C89-400F-854B-53642CB62AC0}
    parent: NULL

Metric - uuid:{6946CE2D-26D8-49FC-8BC3-782D05A1C2BC}
    parent: CommunityOwnedEntity


HTTP-Feature - uuid:{EDCAF240-D0D3-4155-92F5-DA20CABBD439}
    parent: Feature
    
HTTP-Host-Feature - uuid:{C7BE6222-866F-4203-B5AA-F5C3D24D5828}
    parent: HTTP-Feature
    
CONN-Feature - uuid:{76B35AB0-4426-4213-B9FF-872C7F3E80DF}
    parent: Feature

CONN-DestIP-Feature - uuid:{4CCAF3E2-E05B-4337-A242-9539AFB33511}
    parent: CONN-Feature

CONN-SourceIP-Feature - uuid:{9CA1A0A9-A0BA-40DF-A58F-2EF3B8A70864}
    parent: CONN-Feature

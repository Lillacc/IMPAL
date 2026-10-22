classDiagram
    class Roles {
        +int id_role
        +String role_name
        -getRole()
    }

    class Users {
        +int id_user
        +String username
        +String password
        +String email
        +int id_role
        -login()
        -register()
    }

    class News {
        +int id_news
        +String judul
        +Text isi_konten
        +Timestamp tanggal_post
        +int id_author
        -createNews()
    }

    class Player_Match_Stats {
        +int id_stat
        +int id_match
        +int id_user
        +String agent_used
        +int kills
        +int deaths
        +int assists
        +int acs
        -calculateStats()
    }

    class Teams {
        +int id_team
        +String nama_tim
        -createTeam()
    }

    class Team_Members {
        +int id_member
        +int id_user
        +int id_team
        -assignMember()
    }

    class Matches {
        +int id_match
        +int id_tournament
        +int id_team_a
        +int id_team_b
        +String map_name
        +int skor_akhir_a
        +int skor_akhir_b
        +Timestamp jadwal
        -updateMatch()
    }

    class Tournaments {
        +int id_tournament
        +String nama_turnamen
        +String penyelenggara
        -createTournament()
    }

    class Match_Rounds {
        +int id_round
        +int id_match
        +int nomor_ronde
        +int id_pemenang_ronde
        +String metode_menang
        -recordRound()
    }

    class Round_Player_Stats {
        +int id_stat
        +int id_round
        +int id_user
        +int kills
        +boolean death
        +int assists
        +int damage
        +boolean is_clutch
        +boolean is_first_blood
        -insertStat()
    }

    %% Relasi antar Class
    Users --> Roles
    News --o Users
    Player_Match_Stats --> Users
    Player_Match_Stats --* Matches
    Team_Members --> Users
    Team_Members --> Teams
    Matches --> Teams
    Matches --o Tournaments
    Match_Rounds --* Matches
    Match_Rounds --> Teams
    Round_Player_Stats --> Users
    Round_Player_Stats --* Match_Rounds

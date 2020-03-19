# ACS.00048 - Select random independent Duke to rebelion
narrative_event = {
	id = ACS.00048
	is_triggered_only = yes
	hide_window = yes

	immediate = {
		random_playable_ruler = {
			limit = {
				OR = {
					NOT = { has_character_flag = faction_independence_ultimatum_taken }
					had_character_flag = { flag = faction_independence_ultimatum_taken days = 7 }
				}
				liege = {
					independent = yes
				}
			}
			character_event = { id = ACS.00049 }
		}
	}
}

# ACS.00048 - Select random independent Duke to rebelion
narrative_event = {
	id = ACS.00048
	is_triggered_only = yes
	hide_window = yes

	immediate = {
		random_playable_ruler = {
			limit = {
				OR = {
					NOT = { has_character_flag = faction_independence_ultimatum_taken }
					had_character_flag = { flag = faction_independence_ultimatum_taken days = 7 }
				}
				liege = {
					independent = yes
				}
			}
			character_event = { id = ACS.00049 }
		}
	}
}
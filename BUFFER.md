#####################################
######### REPUBLIC EVENTS ###########
#####################################
# ACS.35 - Check for venezia exists
character_event = {
	id = ACS.70
	hide_window = yes
	is_triggered_only = yes
	ai = no

	trigger = {
		has_global_flag = comet_tiamat
		NOT = { has_global_flag = infiltered_venecia }
	}

	immediate = {
		random_character = {
			limit = {
				has_landed_title = c_venezia
				is_merchant_republic = yes
			}
			character_event = { id = ACS.36 }
		}
	}
}

# ACS.36
character_event = {
	id = ACS.36
	hide_window = yes
	is_triggered_only = yes

	immediate = {
		character_event = { id = ACS.37 days = 7 }
		any_vassal = {
			set_character_flag = check_for_dissapears
		}

		random_vassal = {
			limit = {
				is_patrician = yes
				ai = yes
			}
			any_dynasty_member = {
				death = {
					death_reason = death_murder_unknown
				}
			}
			death = {
				death_reason = death_murder_unknown
			}
		}		
	}	
}

# ACS.37 - set new patrician
character_event = {
	id = ACS.37
	hide_window = yes
	is_triggered_only = yes
	
	immediate = {
		set_global_flag = infiltered_venecia
		random_vassal = {
			limit = {
				is_patrician = yes
				ai = yes
				NOT = { has_character_flag = check_for_dissapears }
			}
			character_event = { id = ACS.38 }			
		} 
	}
}    

# ACS.38 - Generate family for the new patrician
character_event = {
    id = ACS.38
    hide_window = yes
    is_triggered_only = yes

    immediate = {
    	set_name = "Dante"
    	add_trait = ambitious
    	wealth = 300
		join_society = pentaghast_society
		set_secret_religion = ishtar_religion
		any_spouse = {
			death = {
				death_reason = death_childbirth
			}
		}
		create_character = {
			female = yes
			age = 23
			trait = fair
			trait = lustful
			trait = cynical
			trait = gregarious
		}
		new_character = {
			set_name = "Beatriz"
			save_event_target_as = generated_patrician_spouse
		}
		add_spouse = event_target:generated_patrician_spouse
		create_character = {
			age = 10				
		}
		new_character = {
			set_father = ROOT
			set_mother =  event_target:generated_patrician_spouse
		}
		create_character = {
			age = 6				
		}
		new_character = {
			set_father = ROOT
			set_mother =  event_target:generated_patrician_spouse
		}
		create_character = {
			age = 0				
		}
		new_character = {
			set_father = ROOT
			set_mother =  event_target:generated_patrician_spouse
		}
    }
}

# ACS.41 - Vee reaches adulthood
character_event = {
	id = ACS.41
	hide_window = yes
	is_triggered_only = yes
	has_character_flag = is_vee

	immediate = {
		ROOT = {
			set_character_flag = do_not_disturb
		}
		pentaghast_society = {
			any_society_member = {
				narrative_event = { id = ACS.42 }
			}
		}
	}
}

# ACS.42 - Society members receive the invitation
narrative_event = {
	id = ACS.42	
	title = EVTNAMEACS.42
	desc = EVTDESCACS.42
	picture = GFX_evt_emissary_byzantine
	is_triggered_only = yes

	immediate = {
		if = {
			limit = {
				prisoner = no
				age >= 18
				is_incapable = no
				NOT = { has_character_flag = do_not_disturb}
			}
			set_character_flag = do_not_disturb			
		}
		FROM = {			
			character_event = { id = ACS.43 } 
		}
	}

	option = {
		name = OK
		ai_chance = { factor = 100 }
	}
}

# ACS.43 - Select a random Pentaghast society member for pollinate Vee
character_event = {
	id = ACS.43
	hide_window = yes
	is_triggered_only = yes

	immediate = {
		pentaghast_society = {
			random_society_member = {
				limit = {
					is_female = no
					is_society_grandmaster = no
				}
				save_event_target_as = selected_pentaghast
				set_character_flag = selected_pentaghast_flag
			}
			any_society_member = {
				narrative_event = { id = ACS.44 }
			}
		}
		ROOT = {
			impregnate_cuckoo = event_target:selected_pentaghast
			set_character_flag = awaken_vee
		}
	}
}

# ACS.44 - Pentaghast members receive notification for accomplished orgiastic ritual
narrative_event = {
	id = ACS.44
	title = EVTNAMEACS.44
	desc = EVTDESCACS.44
	picture = GFX_evt_emissary_byzantine
	is_triggered_only = yes

	immediate = {
		pentaghast_society = {
			random_society_member = {
				limit = {
					has_character_flag = selected_pentaghast_flag
				}
				death = {
					death_reason = death_murder_unknown
				}
			}
		}
	}

	option = {
		name = OK
		ai_chance = { factor = 100 }
	}
}

random_character = {
limit = {
trait = my_trait
has_character_flag = my_flag?
}
save_event_target_as = dont_kill?
}
any_character = {
limit = {
trait = my_trait
has_character_flag = my_flag
NOT = { character = event_target:dont_kill }?
}
death = { death_reason = death_platypus }?}

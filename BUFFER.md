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




# ACS.00062: Vee Fabricate claims
character_event = {
	id = ACS.00062
	is_triggered_only = yes
	hide_window = yes

	min_age = 16
	capable_only = yes
	prisoner = no

	trigger = {
		vee_can_do_council_work_trigger = yes
		liege = {
			is_nomadic = no
		}
	}

	immediate = {
		liege = {
			save_event_target_as = vee_liege
		}
		random_playable_ruler = {
			limit = {
				num_of_vassals > 1
				is_landed = yes
				higher_real_tier_than = BARON
			}
			primary_title = {
				# TO-DO Custom messages for every tier and notification
				add_claim = event_target:vee_liege
			}
		}
	}
}

# ACS.00063 - Vee sows dissent between a local noble and his liege
character_event = {
	id = ACS.00063
	is_triggered_only = yes
	hide_window = yes

	min_age = 16
	capable_only = yes
	prisoner = no

	trigger = {
		vee_can_do_council_work_trigger = yes
	}

	immediate = {
		liege = {
			save_event_target_as = vee_liege
		}
		random_playable_ruler = {
			limit = {
				independent = no
				NOT = { is_vassal_or_below_of = event_target:vee_liege }
			}
			character_event = { id = 20160 days = 7 }
		}
	}
}

# ACS.00064 - Raise taxes from peasants 
character_event = {
	id = ACS.00064
	is_triggered_only = yes
	hide_window = yes

	min_age = 16
	capable_only = yes
	prisoner = no

	trigger = {
		vee_can_do_council_work_trigger = yes
		liege = {
			is_tribal = no
			is_nomadic = no
		}
	}

	immediate = {
		liege = {
			letter_event = { id = 20200 tooltip = "EVTTOOLTIP20200" }
		}
	}
}

# ACS.00065 - Vee convert a province to a ROOT culture - STEWARDSHIP
character_event = {
	id = ACS.00065
	is_triggered_only = yes
	hide_window = yes

	min_age = 16
	capable_only = yes
	prisoner = no

	trigger = {
		vee_can_do_council_work_trigger = yes
		any_realm_province = {
			NOT = { culture = ROOT }
		}
	}

	immediate = {
		random_realm_province = {
			culture = ROOT
		}
		# TO-DO: Notification to the liege
	}
}

# ACS.00066 - Oversee construction - STEWARDSHIP
character_event = {
	id = ACS.00066
	is_triggered_only = yes
	hide_window = yes

	min_age = 16
	capable_only = yes
	prisoner = no

	trigger = {
		vee_can_do_council_work_trigger = yes
	}

	immediate = {
		liege = {
			letter_event = { id = 20230 tooltip = "EVTTOOLTIP20230" }
		}
	}
}

# ACS.00067 - Spawn troops in war - STEWARDSHIP
character_event = {
	id = ACS.00067
	is_triggered_only = yes
	hide_window = yes

	min_age = 16
	capable_only = yes
	prisoner = no

	trigger = {
		vee_can_do_council_work_trigger = yes
		liege = { is_tribal = yes }
	}

	immediate = {
		liege = {
			if = {
				limit = {
					war = yes
				}
				liege = { character_event = { id = 20209 } }
			}
		}
	}
}

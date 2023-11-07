# Experiment-6---Implementation-of-Semantic-Analysis
### Aim :
Construct a python program to read a text from a file.Identify the verbs from the text file and provide synonyms for all verbs using Natutal Language Processing

### Algorithm:
Import the necessary libraries: nltk and wordnet.
Define a function get_verbs(sentence) to identify verbs in a given sentence using part-of-speech tagging.
Define a function get_synonyms(word) to get synonyms for a given word using the WordNet corpus.
Define a function read_text_file(file_path) to read text from a file and return the content as a string.
In the main program:
Set the file_path variable to the path of the input text file.
Read the text from the file using the read_text_file() function.
Tokenize the text into sentences using the sent_tokenize() function from the nltk library.
Initialize an empty list all_verbs to store all identified verbs.
Initialize an empty dictionary synonyms_dict to store the synonyms for each verb.
Iterate over each sentence:
Call the get_verbs() function to identify verbs in the sentence.
Append the identified verbs to the all_verbs list.
For each verb, call the get_synonyms() function to get its synonyms and store them in the synonyms_dict dictionary.
Print the verbs and their synonyms.
Execute the main program.

### PROGRAM
```
Developed By:P.SIva Naga Nithin
Reg.No:212221240037
```
```
import nltk
from nltk.corpus import wordnet

nltk.download('averaged_perceptron_tagger')
nltk.download('wordnet')
nltk.download('punkt')

# Function to identify verbs in a sentence
def get_verbs(sentence):
    verbs = []
    pos_tags = nltk.pos_tag(nltk.word_tokenize(sentence))
    for word, tag in pos_tags:
        if tag.startswith('V'):  # Verbs start with 'V' in the POS tag
            verbs.append(word)
    return verbs


def get_synonyms(word):
    synonyms = []
    for syn in wordnet.synsets(word):
        for lemma in syn.lemmas():
            synonyms.append(lemma.name())
    return synonyms


def read_text_file(file_path):
    with open(file_path, 'r') as file:
        text = file.read()
    return text


def main():
    file_path = 'sample.txt'

    text = read_text_file(file_path)
    sentences = nltk.sent_tokenize(text)

    all_verbs = []
    synonyms_dict = {}

    for sentence in sentences:
        verbs = get_verbs(sentence)
        all_verbs.extend(verbs)
        for verb in verbs:
            synonyms = get_synonyms(verb)
            synonyms_dict[verb] = synonyms

    with open('output.csv', 'w', newline='') as csvfile:
        writer = csv.writer(csvfile)
        writer.writerow(['Verb', 'Synonyms'])
        for verb, synonyms in synonyms_dict.items():
            writer.writerow([verb, ', '.join(synonyms)])


if __name__ == '__main__':
    main()
```
### OUTPUT:

Verb	Synonyms
was	Washington, Evergreen_State, WA, be, be, be, exist, be, be, equal, be, constitute, represent, make_up, comprise, be, be, follow, embody, be, personify, be, be, live, be, cost, be
named	name, call, name, identify, name, nominate, make, appoint, name, nominate, constitute, name, mention, advert, bring_up, cite, name, refer, identify, discover, key, key_out, distinguish, describe, name, list, name, diagnose, name
lived	populate, dwell, live, inhabit, live, survive, last, live, live_on, go, endure, hold_up, hold_out, exist, survive, live, subsist, be, live, know, experience, live, live
loved	love, love, enjoy, love, sleep_together, roll_in_the_hay, love, make_out, make_love, sleep_with, get_laid, have_sex, know, do_it, be_intimate, have_intercourse, have_it_away, have_it_off, screw, fuck, jazz, eff, hump, lie_with, bed, have_a_go_at_it, bang, get_it_on, bonk, loved
explore	research, search, explore, explore, explore, explore
exploring	research, search, explore, explore, explore, explore
came	come, come_up, arrive, get, come, come, come, come, follow, come, issue_forth, come, hail, come, come, come, come, fall, come, come, total, number, add_up, come, amount, come, add_up, amount, come, come_in, occur, come, derive, come, descend, do, fare, make_out, come, get_along, come, come
peered	peer
see	see, see, understand, realize, realise, see, witness, find, see, visualize, visualise, envision, project, fancy, see, figure, picture, image, see, consider, reckon, view, regard, learn, hear, get_word, get_wind, pick_up, find_out, get_a_line, discover, see, watch, view, see, catch, take_in, meet, run_into, encounter, run_across, come_across, see, determine, check, find_out, see, ascertain, watch, learn, see, check, insure, see_to_it, ensure, control, ascertain, assure, see, see, visit, see, attend, take_care, look, see, see, go_steady, go_out, date, see, see, see, see, examine, see, experience, see, go_through, see, escort, see, interpret, construe, see
decided	decide, make_up_one's_mind, determine, decide, settle, resolve, adjudicate, decide, decide, distinct, decided
climb	ascent, acclivity, rise, raise, climb, upgrade, climb, climbing, mounting, climb, mount, climb, climb_up, mount, go_up, climb, wax, mount, climb, rise, climb, climb, rise, go_up, climb
led	light-emitting_diode, LED, lead, take, direct, conduct, guide, leave, result, lead, lead, lead, head, lead, run, go, pass, lead, extend, head, lead, lead, top, contribute, lead, conduce, conduct, lead, direct, go, lead, precede, lead, run, lead, moderate, chair, lead
fell	hide, fell, fell, felled_seam, fell, fell, drop, strike_down, cut_down, fly, fell, vanish, fell, fall, descend, fall, go_down, come_down, fall, fall, come, precipitate, come_down, fall, fall, fall, fall, shine, strike, fall, fall, decrease, diminish, lessen, fall, fall, fall, fall, fall, fall, fall, fall, accrue, fall, fall, light, fall, return, pass, devolve, fall, fall, fall_down, fall, hang, fall, flow, fall, fall, fall, fall, fall, fall, fall, descend, settle, barbarous, brutal, cruel, fell, roughshod, savage, vicious
landed	land, set_down, land, put_down, bring_down, bring, land, land, land, land, set_ashore, shore, down, shoot_down, land, landed
found	found, establish, set_up, found, launch, establish, found, plant, constitute, institute, establish, base, ground, found, find, happen, chance, bump, encounter, detect, observe, find, discover, notice, find, regain, determine, find, find_out, ascertain, find, feel, witness, find, see, line_up, get_hold, come_up, find, discover, find, discover, find, find, rule, find, receive, get, find, obtain, incur, find, recover, retrieve, find, regain, find, find_oneself, find, found
were	be, be, be, exist, be, be, equal, be, constitute, represent, make_up, comprise, be, be, follow, embody, be, personify, be, be, live, be, cost, be
talking	talk, talking, talk, speak, talk, speak, utter, mouth, verbalize, verbalise, speak, talk, spill, talk, spill_the_beans, let_the_cat_out_of_the_bag, talk, tattle, blab, peach, babble, sing, babble_out, blab_out, lecture, talk
had	have, have_got, hold, have, feature, experience, receive, have, get, own, have, possess, get, let, have, consume, ingest, take_in, take, have, have, hold, throw, have, make, give, have, have, have, experience, have, induce, stimulate, cause, have, get, make, accept, take, have, receive, have, suffer, sustain, have, get, have, get, make, give_birth, deliver, bear, birth, have, take, have
learned	learn, larn, acquire, learn, hear, get_word, get_wind, pick_up, find_out, get_a_line, discover, see, memorize, memorise, con, learn, learn, study, read, take, teach, learn, instruct, determine, check, find_out, see, ascertain, watch, learn, erudite, learned, knowing, knowledgeable, learned, lettered, well-educated, well-read, conditioned, learned
arguing	controversy, contention, contestation, disputation, disceptation, tilt, argument, arguing, argue, reason, argue, contend, debate, fence, argue, indicate
do	bash, do, brawl, do, doh, ut, Doctor_of_Osteopathy, DO, make, do, perform, execute, do, do, perform, do, fare, make_out, come, get_along, cause, do, make, practice, practise, exercise, do, suffice, do, answer, serve, do, make, act, behave, do, serve, do, do, manage, dress, arrange, set, do, coif, coiffe, coiffure, do
terrorizing	terrorize, terrorise, terrify, terrorize, terrorise
help	aid, assist, assistance, help, assistant, helper, help, supporter, aid, assistance, help, avail, help, service, help, assist, aid, help, aid, help, facilitate, help_oneself, help, serve, help, help, avail, help, help
defeat	defeat, licking, frustration, defeat, get_the_better_of, overcome, defeat, kill, shoot_down, defeat, vote_down, vote_out
went	travel, go, move, locomote, go, proceed, move, go, go_away, depart, become, go, get, go, run, go, run, go, pass, lead, extend, proceed, go, go, go, sound, go, function, work, operate, go, run, run_low, run_short, go, move, go, run, survive, last, live, live_on, go, endure, hold_up, hold_out, go, die, decease, perish, go, exit, pass_away, expire, pass, kick_the_bucket, cash_in_one's_chips, buy_the_farm, conk, give-up_the_ghost, drop_dead, pop_off, choke, croak, snuff_it, belong, go, go, start, go, get_going, move, go, go, go, blend, go, blend_in, go, lead, fit, go, rifle, go, go, plump, go, fail, go_bad, give_way, die, give_out, conk_out, go, break, break_down
challenged	challenge, dispute, gainsay, challenge, challenge, challenge, take_exception
surprised	surprise, surprise, storm, surprise, surprised
agreed	agree, hold, concur, concord, agree, match, fit, correspond, check, jibe, gibe, tally, agree, harmonize, harmonise, consort, accord, concord, fit_in, agree, agree, agree, agree, agreed, in_agreement
fight	battle, conflict, fight, engagement, fight, fighting, combat, scrap, competitiveness, fight, fight, fight, contend, fight, struggle, fight, oppose, fight_back, fight_down, defend, fight, struggle, crusade, fight, press, campaign, push, agitate
fought	contend, fight, struggle, fight, oppose, fight_back, fight_down, defend, fight, struggle, crusade, fight, press, campaign, push, agitate
defeated	defeated, discomfited, get_the_better_of, overcome, defeat, kill, shoot_down, defeat, vote_down, vote_out, defeated, defeated, disappointed, discomfited, foiled, frustrated, thwarted
saving	economy, saving, rescue, deliverance, delivery, saving, preservation, saving, salvage, salve, relieve, save, save, preserve, save, carry_through, pull_through, bring_through, save, save, lay_aside, save_up, save, make_unnecessary, deliver, redeem, save, spare, save, save, economize, economise, keep_open, hold_open, keep, save, write, save, redemptive, redeeming, saving, saving
threw	throw, throw, shed, cast, cast_off, shake_off, throw, throw_off, throw_away, drop, throw, thrust, give, throw, throw, flip, switch, project, cast, contrive, throw, throw, bewilder, bemuse, discombobulate, throw, hurl, throw, hold, throw, have, make, give, throw, throw, throw, confuse, throw, fox, befuddle, fuddle, bedevil, confound, discombobulate
return	tax_return, income_tax_return, return, return, homecoming, return, coming_back, restitution, return, restoration, regaining, return, return, issue, take, takings, proceeds, yield, payoff, recurrence, return, rejoinder, retort, return, riposte, replication, comeback, counter, return_key, return, return, paying_back, getting_even, return, return, reappearance, return, return, render, return, revert, return, retrovert, regress, turn_back, hark_back, return, come_back, recall, return, take_back, bring_back, return, return, retort, come_back, repay, return, riposte, rejoin, come_back, return, refund, return, repay, give_back, render, deliver, return, reelect, return, fall, return, pass, devolve, return, render, yield, return, give, generate, return
said	state, say, tell, allege, aver, say, suppose, say, read, say, order, tell, enjoin, say, pronounce, articulate, enounce, sound_out, enunciate, say, say, say, say, say, say, aforesaid, aforementioned, said
climbed	climb, climb_up, mount, go_up, climb, wax, mount, climb, rise, climb, climb, rise, go_up, climb
reached	reach, make, attain, hit, arrive_at, gain, reach, hit, attain, reach, reach_out, reach, get_through, get_hold_of, contact, achieve, accomplish, attain, reach, reach, extend_to, touch, reach, make, get_to, progress_to, pass, hand, reach, pass_on, turn_over, give, strive, reach, strain
glad	gladiolus, gladiola, glad, sword_lily, glad, glad, happy, glad, beaming, glad
be	beryllium, Be, glucinium, atomic_number_4, be, be, be, exist, be, be, equal, be, constitute, represent, make_up, comprise, be, be, follow, embody, be, personify, be, be, live, be, cost, be
knew	know, cognize, cognise, know, know, know, know, experience, live, acknowledge, recognize, recognise, know, know, sleep_together, roll_in_the_hay, love, make_out, make_love, sleep_with, get_laid, have_sex, know, do_it, be_intimate, have_intercourse, have_it_away, have_it_off, screw, fuck, jazz, eff, hump, lie_with, bed, have_a_go_at_it, bang, get_it_on, bonk, know, know, know
forget	forget, bury, forget, block, blank_out, draw_a_blank, forget, forget, leave
are	are, ar, be, be, be, exist, be, be, equal, be, constitute, represent, make_up, comprise, be, be, follow, embody, be, personify, be, be, live, be, cost, be
used	use, utilize, utilise, apply, employ, use, habituate, use, expend, use, practice, apply, use, use, used, exploited, ill-used, put-upon, used, victimized, victimised, secondhand, used
explored	research, search, explore, explore, explore, explore
tell	Tell, William_Tell, state, say, tell, tell, tell, narrate, recount, recite, order, tell, enjoin, say, tell, assure, tell, tell, evidence, distinguish, separate, differentiate, secern, secernate, severalize, severalise, tell, tell_apart
create	make, create, create, create, create, create, make, produce, make, create
show	show, display, show, show, appearance, show, show, demo, exhibit, present, demonstrate, prove, demonstrate, establish, show, shew, testify, bear_witness, prove, evidence, show, show, picture, depict, render, show, express, show, evince, indicate, point, designate, show, show, show_up, read, register, show, record, show, usher, show, show

### RESULT:

Thus, we have successfully implemented a program for Natural Language Processing.


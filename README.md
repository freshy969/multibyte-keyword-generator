# Multibyte Keyword Generator

[![Downloads](https://img.shields.io/packagist/dt/peterkahl/multibyte-keyword-generator.svg)](https://packagist.org/packages/peterkahl/multibyte-keyword-generator)
[![License](http://img.shields.io/:license-apache-blue.svg)](http://www.apache.org/licenses/LICENSE-2.0.html)
[![If this project has business value for you then don't hesitate to support me with a small donation.](https://img.shields.io/badge/Donations-via%20Paypal-blue.svg)](https://www.paypal.me/PeterK93)

Inspired by a package by [Ver Pangonilo](http://www.phpclasses.org/browse/package/3245.html) with additional improvements, among them being better word segmentation and ability to handle multibyte strings.

This library generates keywords based on the contents of a text string. This eliminates the tedious
process of thinking what the best keywords are. The main principle of
this method is the frequency (number of occurrences) of single words or multiple
words in a text string.

The string supplied to this class may contain HTML tags and
punctuations. Advantage is taken from the presence of line breaks and
punctuations to better guess the best multiple word keyphrases.

This Keyword Generator will automatically create single word
keywords, 2-word and 3-word keyphrases. All keywords and keyphrases are
filtered to remove common (useless) words. Common words are defined
within the class and can be associated with specific language.

## Usage

```php
use peterkahl\KeywordGenerator\KeywordGenerator;

$kwObj = new KeywordGenerator;
$str   = 'At the university of Paris Nanterre, on the outskirts of the French capital, Antoine Guerreiro of the union of communist students was handing out leaflets urging students to vote for Emmanuel Macron in the final round of the presidential election next Sunday.

Or, to be strictly accurate, to vote against the Front National’s Marine Le Pen. Guerreiro can find very little – if anything – to support in Macron’s programme, but needs must. The alternative is worse.

“On Sunday night, we were all shaken, but now we must carry on without denying our ideals; and one of our strongest ideals is to oppose the far right in all circumstances,” Geurreiro, 19, said. “It’s clear.”

The students are opposing the “ni-ni” (neither-nor) option of abstaining, voting blank or spoiling the ballot paper. Others call it the “ni patrie, ni patron” choice, a rejection of Le Pen’s nationalism and Macron’s support of bankers and bosses.

The leaflet in Guerreiro’s hand said: “After a campaign marked by scandal, neoliberalism and the extreme right … it would be tempting not to turn out for the second round. However, it would not be sensible to let the extreme right run our country.”

The former Socialist mayor of Paris, Bertrand Delanoë, told RTL radio he would follow his party’s call to vote for Macron, reminding listeners: “Hitler was elected by universal suffrage. I don’t want to make anyone feel guilty. I’m calling for responsibility, conscience … and generosity. At this given moment we have to put France before our old resentments.”

The conservative Les Républicains party, whose presidential candidate François Fillon was defeated in the first round, has also called for an electoral “barrage” against Le Pen, though some in its traditional Catholic right wing have drifted to the far right.

Even Macron’s arch-nemesis, sheep farmer José Bové, the European ecologist MP and anti-globalisation militant famous for once dismantling a McDonalds restaurant, said he would vote for the En Marche! candidate “without ambiguity or hesitation”. Bové said he had no time for “leftwing purists” like the hard-left firebrand, Jean-Luc Mélenchon. But where was Mélenchon, charismatic leader of La France Insoumise (the France Unbowed) movement? And what would he advise his seven million voters to do?

To refuse to choose between a banker and a fascist is an affront to democracy and history
 Read more
As the clamour for Mélenchon to speak last week grew, his team said that he was not “a guru” and would not be telling anyone how to vote, while insisting that a vote for Marine Le Pen was “not an option”.

With the question of whether to vote and how causing anguish and anger in equal measure among the hardline French left, for whom Macron is unpalatable and Le Pen beyond the political pale. Jean-Yves Camus, a political analyst with the left-leaning Jean Jaurès foundation and expert on the far right, said waverers needed to be clear in their minds what is at stake.

“This is a choice of civilisation. It’s not a choice between two different programmes or two different political figures. Let’s be completely honest, this is the choice between two kinds of France. That is what’s at stake,” Camus said.

Comparisons with 2002, when the FN founder, Jean-Marie Le Pen, knocked out the Socialist party candidate, Lionel Jospin, in the first round of the presidential election, are misleading. The 2002 result was a shock to France and Le Pen himself; he had no credible programme and no real ambition to be president. And in the second round, France voted massively for the conservative Jacques Chirac.

Today no one doubts Marine Le Pen’s will to win. Camus warned that, despite the younger Le Pen’s attempts to clean up the FN’s racist, Holocaust-denying image, the difference between her and her father in political terms was purely cosmetic. “If you listen closely, the words are different, but the policies are the same. Jean-Marie Le Pen said ‘France for the French’, Marine Le Pen says ‘France first’ and her supporters chant: ‘This is our home’,” Camus told a meeting of the Anglo-American Press Association. “We have no choice; we have to stop Le Pen. The spectre of neofascism is still there.”

And he added: “We will probably hear many nasty things in the coming week; nasty stuff about Macron being a former Rothschild banker, for example.”

Harry Bernas, a retired physicist and Mélenchon supporter, said he would be voting Macron because “the danger of abstaining is too great. There is something temporarily irreversible about having Le Pen come to power.

“Thanks to Jean-Luc Mélenchon people have begun thinking there’s another way out of this crisis of poverty, unemployment, despair. The real question is how to vote to keep that going. In my mind it will be easier to continue the fight under Macron than Le Pen, who is more dangerous,” said Bernas.

Joseline Frommer, 68, a former legal assistant and one-time Socialist supporter who also voted for Mélenchon in the first round, admitted she was in the “ni-ni” camp and will vote blank unless the final opinion polls on Friday show that Le Pen could win.

“It’s impossible for me to vote for Le Pen, but a vote for Macron? If I do and he has a huge majority, I think it will make me physically sick. But it’s true, we cannot take the risk of Le Pen winning,” she said.

In Le Monde, Gérard Miller, a psychoanalyst and writer, said Mélenchon supporters like himself were not going to take “moral lessons in anti-fascism”.

“That Macron is today a temporary, very temporary alas, rampart against the Front National, I can admit because I’m going to vote for the leader of En Marche!, but only if we’re going to be lucid: in terms of fighting the far right, nothing, starting with his programme and his past, goes in favour of the former economy minister,” Miller wrote.

Latest polling suggests only 40% of Mélenchon voters will vote for Macron, 45% will abstain, while 15% will vote for Le Pen. On Friday, Mélenchon broke his self-imposed silence to announce he would be voting, but how was between him and the ballot box. This week his campaign team will present the result of a consultation of 450,000 supporters, “Les Insoumis” (the Unbowed), on three choices: to abstain, vote blank or vote for Macron. Mélenchon’s spokesman, Alexis Corbière, said none of the three options for the second round run-off was “immoral”.

Before then, there could be a repeat of last week clashes between police and “anti-fascist” protesters as demonstrators take to the streets across France for the traditional May Day workers’ marches. On Twitter, the #JeVoteMacron (I’m voting Macron) versus the #SansMoiLe7mai (Without me on 7 May), vote or abstain battle continues.

Whatever happens next Sunday, Harry Bernas says the crisis in France is “so bad, so deep and the need for change so great” that the country is at boiling point. “It’s what we physicists call first order transition; when you heat water there’s a change you hardly see just before it turns into vapour, that fluctuation, the agitation around the edge, we’re at that stage, and I think there’s very little chance it will be a subtle, kind or friendly transition.”
';

$kwObj->lang = 'en';
echo $kwObj->generateKW($str); # macron,round,right,choice,france,first,mélenchon,second round,vote macron,first round

```
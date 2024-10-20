1) Program to find the minimum and maximum value between two inputs:

 % min(X, Y, Min): Min is the minimum of X and Y
min(X, Y, X) :- X =< Y.
min(X, Y, Y) :- X > Y.

% max(X, Y, Max): Max is the maximum of X and Y
max(X, Y, X) :- X >= Y.
max(X, Y, Y) :- X < Y.

You can test the above rules with queries like:
?- min(5, 10, Min).
Min = 5.

?- max(5, 10, Max).
Max = 10.
////////////////////////////////////////
2)% Gender facts
male(swarit).
male(arnav).
male(ayansh).
male(meet).
female(tirtha).
female(viha).
female(marvi).
female(durva).

% Parent-child facts
parent(swarit, tirtha).
parent(swarit, arnav).
parent(arnav, ayansh).
parent(arnav, meet).
parent(arnav, viha).
parent(tirtha, marvi).
parent(marvi, durva).


% Mother: A mother is a female parent
mother(X, Y) :- female(X), parent(X, Y).

% Father: A father is a male parent
father(X, Y) :- male(X), parent(X, Y).

% Sibling: Two people are siblings if they share a parent
sibling(X, Y) :- parent(Z, X), parent(Z, Y), X \= Y.

% Aunt: A female is an aunt if she is a sibling of a parent
aunt(X, Y) :- female(X), sibling(X, Z), parent(Z, Y).

% Uncle: A male is an uncle if he is a sibling of a parent
uncle(X, Y) :- male(X), sibling(X, Z), parent(Z, Y).

% Grandparent: A grandparent is a parent of a parent
grandparent(X, Y) :- parent(X, Z), parent(Z, Y).

% Cousin: Two people are cousins if their parents are siblings
cousin(X, Y) :- parent(Z, X), parent(W, Y), sibling(Z, W).








?- parent(swarit, Child).
?- sibling(arnav, Sibling).
?- grandparent(Grandparent, ayansh).
?- mother(marvi, durva).
?- uncle(Uncle, viha).

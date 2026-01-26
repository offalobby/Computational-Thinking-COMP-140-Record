## Recipe: MakeCircleThroughThreePoints

**Inputs** 

* `point0x`, `point0y` : real numbers, the coordinates of point (P_0)
* `point1x`, `point1y` : real numbers, the coordinates of point (P_1)
* `point2x`, `point2y` : real numbers, the coordinates of point (P_2)

**Preconditions**

* The three points are not collinear (so a unique circle exists).
* For any pair of points used to compute a slope, the slope computation is defined (i.e., the two points do not have the same (x)-value).
* Any other helper preconditions required by your helper operations (midpoint, slope, perpendicular-line, line-intersection, distance) must hold.

**Outputs**

* `centerx`, `centery` : real numbers, the coordinates of the circle’s center (C)
* `radius` : a nonnegative real number, the circle’s radius (r)

---

### Steps

1. **Compute midpoint of the segment from (P_0) to (P_1).**
   Let
   [
   mid0x \leftarrow \frac{point0x + point1x}{2},\quad
   mid0y \leftarrow \frac{point0y + point1y}{2}.
   ]

2. **Compute midpoint of the segment from (P_1) to (P_2).**
   Let
   [
   mid1x \leftarrow \frac{point1x + point2x}{2},\quad
   mid1y \leftarrow \frac{point1y + point2y}{2}.
   ]

3. **Compute slope of the line through (P_0) and (P_1).**
   Let
   [
   slope0 \leftarrow \frac{point1y - point0y}{point1x - point0x}.
   ]

4. **Compute slope of the line through (P_1) and (P_2).**
   Let
   [
   slope1 \leftarrow \frac{point2y - point1y}{point2x - point1x}.
   ]

5. **Compute slopes of the perpendicular bisectors.**
   Let `perp0` be the slope of a line perpendicular to the line with slope `slope0`.
   Let `perp1` be the slope of a line perpendicular to the line with slope `slope1`.
   (For nonzero slopes, a perpendicular slope is the negative reciprocal.)

6. **Form the two perpendicular-bisector lines.**

   * Line (L_0): the line with slope `perp0` that passes through ((mid0x, mid0y)).
   * Line (L_1): the line with slope `perp1` that passes through ((mid1x, mid1y)).

7. **Find the intersection of the two perpendicular bisectors.**
   Let ((centerx, centery)) be the intersection point of (L_0) and (L_1).
   (This point exists and is unique if the original points are not collinear.)

8. **Compute the radius as the distance from the center to one of the original points (e.g., (P_0)).**
   Let
   [
   radius \leftarrow \sqrt{(centerx - point0x)^2 + (centery - point0y)^2}.
   ]

9. **Return the center and radius.** 
   Output `centerx`, `centery`, `radius`.
